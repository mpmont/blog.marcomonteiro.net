---











<!--more-->

The problem was in my SSH password. I thought it was this one:

    u. vagrant
	p. vagrant
	
But for some reason it wasn't (yes it was left it as the default one from PuPHPet). So for consistency now everytime I do a fresh install I  always do a few things; Access my machine via SSH. 

        $ vagrant ssh

Changing the way your server deals with mysql connections.

        $ sudo nano /etc/mysql/my.cnf   

Here you want to find the bindaddress setting which will be set to 127.0.0.0 and change it to 0.0.0.0. Don't forget to restart the mysql server after this.

        $ sudo service mysql restart


Anythins left to do is change your password to "vagrant" for consistency.

        $ passwd

That's it, now you can connect without any problems via SSH tunnel to your mysql.