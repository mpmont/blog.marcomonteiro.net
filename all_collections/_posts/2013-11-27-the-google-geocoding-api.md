---
layout: post
title: The Google Geocoding API
date: 2013-11-27
tag: api,code,geocoding,google,maps,tips
description: Geocoding is the process of converting addresses (like "1600 Amphitheatre Parkway, Mountain View, CA") into geographic coordinates (like latitude 37.423021 and longitude -122.083739), which you can use to place markers
author: Marco Monteiro
categories: [api,code,geocoding,google,maps,tips]
---

Geocoding is the process of converting addresses (like "1600 Amphitheatre Parkway, Mountain View, CA") into geographic coordinates (like latitude 37.423021 and longitude -122.083739), which you can use to place markers or position the map.

Reverse geocoding is the process of converting geographic coordinates into a human-readable address.

<!--more-->

**Geocoding Requests**

A Geocoding API request must be of the following form:

	http://maps.googleapis.com/maps/api/geocode/output?parameters

where output may be either of the following values:

* <i class="icon-angle-right"></i> *json* (recommended) indicates output in JavaScript Object Notation
* <i class="icon-angle-right"></i> *xml* indicates output as XML

To access the Geocoding API over HTTPS, use:

	https://maps.googleapis.com/maps/api/geocode/output?parameters

**Required parameters**

**address** - The address that you want to geocode. 
 
**latlng** - The textual latitude/longitude value for which you wish to obtain the closest, human-readable address. See Reverse Geocoding for more information. 

**components** - A component filter for which you wish to obtain a geocode. See Component Filtering for more information. The components filter will also be accepted as an optional parameter if an address is provided.

**sensor** - Indicates whether or not the geocoding request comes from a device with a location sensor. This value must be either true or false.

**Optional parameters**

**bounds** - The bounding box of the viewport within which to bias geocode results more prominently. This parameter will only influence, not fully restrict, results from the geocoder. (For more information see Viewport Biasing below.)

**language** - The language in which to return results. See the list of supported domain languages. Note that we often update supported languages so this list may not be exhaustive. If language is not supplied, the geocoder will attempt to use the native language of the domain from which the request is sent wherever possible.

**region** - The region code, specified as a ccTLD ("top-level domain") two-character value. This parameter will only influence, not fully restrict, results from the geocoder. (For more information see Region Biasing below.)

**components** - The component filters, separated by a pipe (|). Each component filter consists of a component:value pair and will fully restrict the results from the geocoder. For more information see Component Filtering, below.

**Geocoding Responses**

Geocoding responses are returned in the format indicated by the output flag within the URL request's path.

**JSON Output Formats**

In this example, the Geocoding API requests a json response for a query on "1600 Amphitheatre Parkway, Mountain View, CA":

	http://maps.googleapis.com/maps/api/geocode/json?address=1600+Amphitheatre+Parkway,+Mountain+View,+CA&sensor=true_or_false

We've left the sensor parameter in this example as a variable true_or_false to emphasize that you must set this value to either true or false explicitly.

The JSON returned by this request is shown below. Note that actual JSON may contain less whitespace. You should not make assumptions about the amount or format of whitespace between requests.

	{
		{
   		"results" : [
      	{
         "address_components" : [
            {
               "long_name" : "1600",
               "short_name" : "1600",
               "types" : [ "street_number" ]
            },
            {
               "long_name" : "Amphitheatre Pkwy",
               "short_name" : "Amphitheatre Pkwy",
               "types" : [ "route" ]
            },
            {
               "long_name" : "Mountain View",
               "short_name" : "Mountain View",
               "types" : [ "locality", "political" ]
            },
            {
               "long_name" : "Santa Clara",
               "short_name" : "Santa Clara",
               "types" : [ "administrative_area_level_2", "political" ]
            },
            {
               "long_name" : "California",
               "short_name" : "CA",
               "types" : [ "administrative_area_level_1", "political" ]
            },
            {
               "long_name" : "United States",
               "short_name" : "US",
               "types" : [ "country", "political" ]
            },
            {
               "long_name" : "94043",
               "short_name" : "94043",
               "types" : [ "postal_code" ]
            }
         ],
         "formatted_address" : "1600 Amphitheatre Pkwy, Mountain View, CA 94043, USA",
         "geometry" : {
            "location" : {
               "lat" : 37.42291810,
               "lng" : -122.08542120
            },
            "location_type" : "ROOFTOP",
            "viewport" : {
               "northeast" : {
                  "lat" : 37.42426708029149,
                  "lng" : -122.0840722197085
               },
               "southwest" : {
                  "lat" : 37.42156911970850,
                  "lng" : -122.0867701802915
               }
            }
         },
         "types" : [ "street_address" ]
      }
   	],
   	"status" : "OK"
	}


**XML Output Formats**

In this example, the Geocoding API requests an xml response for the identical query shown above for "1600 Amphitheatre Parkway, Mountain View, CA":

	http://maps.googleapis.com/maps/api/geocode/xml?address=1600+Amphitheatre+Parkway,+Mountain+View,+CA&sensor=true_or_false
	
The XML returned by this request is shown below.

	<GeocodeResponse>
		 <status>OK</status>
		 <result>
		 	<type>street_address</type>
	  		<formatted_address>1600 Amphitheatre Pkwy, Mountain View, CA 94043, USA</formatted_address>
  			<address_component>
	   			<long_name>1600</long_name>
   				<short_name>1600</short_name>
	   			<type>street_number</type>
  			</address_component>
  			<address_component>
   				<long_name>Amphitheatre Pkwy</long_name>
   				<short_name>Amphitheatre Pkwy</short_name>
   				<type>route</type>
  			</address_component>
  			<address_component>
   				<long_name>Mountain View</long_name>
   				<short_name>Mountain View</short_name>
   				<type>locality</type>
   				<type>political</type>
  			</address_component>
  			<address_component>
   				<long_name>San Jose</long_name>
   				<short_name>San Jose</short_name>
   				<type>administrative_area_level_3</type>
   				<type>political</type>
  			</address_component>
  			<address_component>
   				<long_name>Santa Clara</long_name>
   				<short_name>Santa Clara</short_name>
   				<type>administrative_area_level_2</type>
   				<type>political</type>
  			</address_component>
  			<address_component>
   				<long_name>California</long_name>
   				<short_name>CA</short_name>
   				<type>administrative_area_level_1</type>
   				<type>political</type>
  			</address_component>
  			<address_component>
   				<long_name>United States</long_name>
   				<short_name>US</short_name>
   				<type>country</type>
   				<type>political</type>
  			</address_component>
  			<address_component>
   				<long_name>94043</long_name>
   				<short_name>94043</short_name>
   				<type>postal_code</type>
  			</address_component>
  			<geometry>
   				<location>
    				<lat>37.4217550</lat>
    				<lng>-122.0846330</lng>
   				</location>
   				<location_type>ROOFTOP</location_type>
   				<viewport>
    				<southwest>
     					<lat>37.4188514</lat>
     					<lng>-122.0874526</lng>
    				</southwest>
    				<northeast>
     					<lat>37.4251466</lat>
     					<lng>-122.0811574</lng>
    				</northeast>
   				</viewport>
  			</geometry>
 		</result>
	</GeocodeResponse>
	
**Reverse Geocoding (Address Lookup)**

The term geocoding generally refers to translating a human-readable address into a location on a map. The process of doing the converse, translating a location on the map into a human-readable address, is known as reverse geocoding.

The Geocoding API supports reverse geocoding directly using the latlng parameter. For example, the following query contains the latitude/longitude value for a location in Brooklyn:

	http://maps.googleapis.com/maps/api/geocode/json?latlng=40.714224,-73.961452&sensor=true_or_false
	
This query returns the following result:

	{
  		"status": "OK",
  		"results": [ {
    		"types": street_address,
    		"formatted_address": "275-291 Bedford Ave, Brooklyn, NY 11211, USA",
    		"address_components": [ {
      			"long_name": "275-291",
      			"short_name": "275-291",
      			"types": street_number
    		}, {
      			"long_name": "Bedford Ave",
      			"short_name": "Bedford Ave",
      			"types": route
    		}, {
      			"long_name": "New York",
      			"short_name": "New York",
      			"types": [ "locality", "political" ]
    		}, {
      			"long_name": "Brooklyn",
      			"short_name": "Brooklyn",
      			"types": [ "administrative_area_level_3", "political" ]
    		}, {
      			"long_name": "Kings",
      			"short_name": "Kings",
      			"types": [ "administrative_area_level_2", "political" ]
    		}, {
      			"long_name": "New York",
      			"short_name": "NY",
      			"types": [ "administrative_area_level_1", "political" ]
    		}, {
      			"long_name": "United States",
      			"short_name": "US",
      			"types": [ "country", "political" ]
    		}, {
      			"long_name": "11211",
      			"short_name": "11211",
      			"types": postal_code
    		} ],
    			"geometry": {
      				"location": {
        			"lat": 40.7142298,
			        "lng": -73.9614669
			    },
      			"location_type": "RANGE_INTERPOLATED",
      			"viewport": {
        			"southwest": {
          				"lat": 40.7110822,
 				        "lng": -73.9646145
        		},
        		"northeast": {
          			"lat": 40.7173774,
          			"lng": -73.9583193
        		}
      		}
    	}
  	},
	... Additional results[] ...
	
Note that the reverse geocoder returned more than one result. The result's "formatted_addresses" are not just postal addresses, but any way to geographically name a location. For example, when geocoding a point in the city of Chicago, the geocoded point may be denoted as a street address, as the city (Chicago), as its state (Illinois) or as a country (The United States). All are "addresses" to the geocoder. The reverse geocoder returns any of these types as valid results.

The reverse geocoder matches political entities (countries, provinces, cities and neighborhoods), street addresses, and postal codes.

The full list of formatted_address values returned by the previous query are shown below.

	"formatted_address": "275-291 Bedford Ave, Brooklyn, NY 11211, USA",
	"formatted_address": "Williamsburg, NY, USA",
	"formatted_address": "New York 11211, USA",
	"formatted_address": "Kings, New York, USA",
	"formatted_address": "Brooklyn, NY, USA",
	"formatted_address": "New York, NY, USA",
	"formatted_address": "New York, USA",
	"formatted_address": "United States"
	
**Region Biasing**

The Google Geocoding API returns address results influenced by the region (typically the country) from which the request is sent. For example, searches for "San Francisco" may return different results if sent from a domain within the United States than one sent from Spain.

You can set the Geocoding API to return results biased to a particular region using the region parameter. This parameter takes a ccTLD (country code top-level domain) argument specifying the region bias. Most ccTLD codes are identical to ISO 3166-1 codes, with some notable exceptions. For example, the United Kingdom's ccTLD is "uk" (.co.uk) while its ISO 3166-1 code is "gb" (technically for the entity of "The United Kingdom of Great Britain and Northern Ireland").

Geocoding results can be biased for every domain in which the main Google Maps application is officially launched. Note that biasing only prefers results for a specific domain; if more relevant results exist outside of this domain, they may be included.

For example, a geocode for "Toledo" returns this result, as the default domain for the Geocoding API is set to the United States:

	http://maps.googleapis.com/maps/api/geocode/json?address=Toledo&sensor=false
	# Returns:
	#
	{
	  "status": "OK",
	  "results": [ {
	    "types": [ "locality", "political" ],
	    "formatted_address": "Toledo, OH, USA",
	    "address_components": [ {
	      "long_name": "Toledo",
	      "short_name": "Toledo",
	      "types": [ "locality", "political" ]
	    }, {
	      "long_name": "Ohio",
	      "short_name": "OH",
	      "types": [ "administrative_area_level_1", "political" ]
	    }, {
   		   "long_name": "United States",
   	   	   "short_name": "US",
    	   "types": [ "country", "political" ]
	    } ],
	    	"geometry": {
	      	"location": {
        	"lat": 41.6529200,
        	"lng": -83.5777820
      	},
      	"location_type": "APPROXIMATE",
      	"viewport": {
        	"southwest": {
          	"lat": 41.5861889,
          	"lng": -83.7058414
        },
        "northeast": {
          	"lat": 41.7195821,
          	"lng": -83.4497226
        }
      },
      "bounds": {
        	"southwest": {
          		"lat": 41.5803170,
          		"lng": -83.6947540
        	},
        	"northeast": {
          		"lat": 41.7326310,
          		"lng": -83.4545660
        	}
      	}
    	}
  	} ]
	}

However, a geocode for "Toledo" with region=es (Spain) will return the Spanish city.

**Component Filtering**

The Google Geocoding API can return address results restricted to a specific area. The restriction is specified using the components filter. A filter consists of a list of component:value pairs separated by a pipe (|). Only the results that match all the filters will be returned. Filter values support the same methods of spelling correction and partial matching as other geocoding requests. If a geocoding result is a partial match for a component filter it will contain a partial_match field in the response.

The components that can be filtered include:

* <i class="icon-angle-right"></i> route matches long or short name of a route.
* <i class="icon-angle-right"></i> locality matches against both locality and sublocality types.
* <i class="icon-angle-right"></i> administrative_area matches all the administrative_area levels.
* <i class="icon-angle-right"></i> postal_code matches postal_code and postal_code_prefix.
* <i class="icon-angle-right"></i> country matches a country name or a two letter ISO 3166-1 country code.

A geocode for "Santa Cruz" with components=country:ES will return Santa Cruz de Tenerife in Canary Islands, Spain.