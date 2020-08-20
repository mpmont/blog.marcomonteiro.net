---
layout: post
title: Php magic methods - The complete guide
date: 2012-10-07
tag: magic methods,oop,php
description: PHP has a few magic methods that you can use in OOP (Object oriented programming). All of them must be identified with two underscore prefix and they act as interceptors
author: Marco Monteiro
categories: [magic methods,oop,php]
---

PHP has a few ‘magic’ methods that you can use in OOP (Object oriented programming). All of them must be identified with two underscore prefix and they act as interceptors that will run then certain required conditions are met. So as you can see these methods are extremely useful.
<!--more-->

**List of magic methods**

The function names __construct(), __destruct(), __call(), __callStatic(), __get(), __set(), __isset(), __unset(), __sleep(), __wakeup(), __toString(), __invoke(), __set_state() and __clone() are magical in PHP classes. You cannot have functions with these names in any of your classes unless you want the magic functionality associated with them.

**Caution**

PHP reserves all function names starting with __ as magical. It is recommended that you do not use function names with __  in PHP unless you want some documented magic functionality.

**__constructor() and __destructor()**

Classes which have a constructor method call this method on each newly-created object, so it is suitable for any initialization that the object may need before it is used. Opposed to that the destructor method will be called as soon as there are no other references to a particular object, or in any order during the shutdown sequence.

	class MyDestructableClass {
	   function __construct() {
		   print "In constructor\n";
		   $this->name = "MyDestructableClass";
	   }

	   function __destruct() {
		   print "Destroying " . $this->name . "\n";
	   }
	}

	$obj = new MyDestructableClass();

**__call() and __callStatic()**

'Call' is triggered when invoking inaccessible methods in an object context. For methods in a static context you should use 'callStatic'.

	class MethodTest
	{
		public function __call($name, $arguments)
		{
			// Note: value of $name is case sensitive.
			echo "Calling object method '$name' "
				 . implode(', ', $arguments). "\n";
		}

		public static function __callStatic($name, $arguments)
		{
			// Note: value of $name is case sensitive.
			echo "Calling static method '$name' "
				 . implode(', ', $arguments). "\n";
		}
	}

	$obj = new MethodTest;
	$obj->runTest('in object context');

	MethodTest::runTest('in static context');

**__get(), __set(), __isset() and __unset()**

'set' is run when writing data to inaccessible properties. 'get' is utilized for reading data from inaccessible properties. 'isset' is triggered by calling isset() or empty() on inaccessible properties. 'unset' is invoked when unset() is used on inaccessible properties.

	class PropertyTest
	{
		/**  Location for overloaded data.  */
		private $data = array();

		/**  Overloading not used on declared properties.  */
		public $declared = 1;

		/**  Overloading only used on this when accessed outside the class.  */
		private $hidden = 2;

		public function __set($name, $value)
		{
			echo "Setting '$name' to '$value'\n";
			$this->data[$name] = $value;
		}

		public function __get($name)
		{
			echo "Getting '$name'\n";
			if (array_key_exists($name, $this->data)) {
				return $this->data[$name];
			}

			$trace = debug_backtrace();
			trigger_error(
				'Undefined property via __get(): ' . $name .
				' in ' . $trace[0]['file'] .
				' on line ' . $trace[0]['line'],
				E_USER_NOTICE);
			return null;
		}

		/**  As of PHP 5.1.0  */
		public function __isset($name)
		{
			echo "Is '$name' set?\n";
			return isset($this->data[$name]);
		}

		/**  As of PHP 5.1.0  */
		public function __unset($name)
		{
			echo "Unsetting '$name'\n";
			unset($this->data[$name]);
		}

		/**  Not a magic method, just here for example.  */
		public function getHidden()
		{
			return $this->hidden;
		}
	}

You have to be careful with this one, because if you don’t specify __isset() and rely just on __get() while using isset() or empty(), you’re in for some bad time.

**Note:**

It is not possible to use overloaded properties in other language  constructs than isset().  This means if empty() is called on  an overloaded property, the overloaded method is  not called.  To workaround that limitation, the overloaded property must be copied into  a local variable in the scope and then be handed to empty().

**__sleep() and __wakeup()**

**Note:**

It is not possible for __sleep() to return names of private properties in parent classes. Doing this will result in an E_NOTICE level error. Instead you may use the Serializable interface. The intended use of __sleep() is to commit pending data or perform similar cleanup tasks. Also, the function is useful if you have very large objects which do not need to be saved completely. As for __wakeup() is to reestablish any database connections that may have been lost during serialization and perform other reinitialization tasks.

	class Connection
	{
		protected $link;
		private $server, $username, $password, $db;

		public function __construct($server, $username, $password, $db)
		{
			$this->server = $server;
			$this->username = $username;
			$this->password = $password;
			$this->db = $db;
			$this->connect();
		}

		private function connect()
		{
			$this->link = mysql_connect($this->server, $this->username, $this->password);
			mysql_select_db($this->db, $this->link);
		}

		public function __sleep()
		{
			return array('server', 'username', 'password', 'db');
		}

		public function __wakeup()
		{
			$this->connect();
		}
	}

**__toString()**

The __toString() method allows a class to decide how it will react when it is treated like a string. For example, what echo $obj; will print. This method must return a string, as otherwise a fatal E_RECOVERABLE_ERROR level error is emitted.

	class TestClass
	{
		public $foo;

		public function __construct($foo)
		{
			$this->foo = $foo;
		}

		public function __toString()
		{
			return $this->foo;
		}
	}

	$class = new TestClass('Hello');
	echo $class;

**__invoke()**

The __invoke() method is called when a script tries to call an object as a function.

	class CallableClass
	{
		public function __invoke($x)
		{
			var_dump($x);
		}
	}
	$obj = new CallableClass;
	$obj(5);
	var_dump(is_callable($obj));

**__set_state()**

Static object __set_state ( array $properties ) This static method is called for classes exported by var_export() since PHP 5.1.0. The only parameter of this method is an array containing exported properties in the form array(‘property’ => value, …).

	class A
	{
		public $var1;
		public $var2;

		public static function __set_state($an_array) // As of PHP 5.1.0
		{
			$obj = new A;
			$obj->var1 = $an_array['var1'];
			$obj->var2 = $an_array['var2'];
			return $obj;
		}
	}

	$a = new A;
	$a->var1 = 5;
	$a->var2 = 'foo';

	eval('$b = ' . var_export($a, true) . ';'); // $b = A::__set_state(array(
												//    'var1' => 5,
												//    'var2' => 'foo',
												// ));

**__clone()**

Creating a copy of an object with fully replicated properties is not always the wanted behavior. A good example of the need for copy constructors, is if you have an object which represents a GTK window and the object holds the resource of this GTK window, when you create a duplicate you might want to create a new window with the same properties and have the new object hold the resource of the new window. Another example is if your object holds a reference to another object which it uses and when you replicate the parent object you want to create a new instance of this other object so that the replica has its own separate copy.

An object copy is created by using the clone keyword (which calls the object’s __clone() method if possible). An object’s __clone() method cannot be called directly.

	class SubObject
	{
		static $instances = 0;
		public $instance;

		public function __construct() {
			$this->instance = ++self::$instances;
		}

		public function __clone() {
			$this->instance = ++self::$instances;
		}
	}

	class MyCloneable
	{
		public $object1;
		public $object2;

		function __clone()
		{
			// Force a copy of this->object, otherwise
			// it will point to same object.
			$this->object1 = clone $this->object1;
		}
	}

	$obj = new MyCloneable();

	$obj->object1 = new SubObject();
	$obj->object2 = new SubObject();

	$obj2 = clone $obj;


	print("Original Object:\n");
	print_r($obj);

	print("Cloned Object:\n");
	print_r($obj2);

This is a complete guide for the magic methods in PHP. All the examples are from the php.net website. I hope this can be useful to other PHP developers just starting the world of OOP.