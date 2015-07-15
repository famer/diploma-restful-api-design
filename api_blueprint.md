FORMAT: 1A
HOST: http://46.101.171.216:8080

# Places
Places API is a service for managing your stored places. 

Usual workflow(all iteractions should be TLS enabled):

    - Device creates user  
    (device uses created user `id` as username for Basic HTTP Auth)
    - Create place(/places POST)
    - Get list of places(/places GET)  
    behold created place
    - One place iteractions:
        - Update place info(/places/0 PUT)
        - Get separate place(/places/0 GET)
        - Remove place(/places/0 DELETE)

## Users Collection [/users]

### Create User [POST]

+ Request (application/json)

        {
            
        }
    
+ Response 201

        {
          "id" : "553503e6e4b0e3b90bca2e5a",
          "username" : null,
          "password" : "",
          "deviceID" : null,
          "token" : null,
          "places" : [ ]
        }

## User's places [/users/{user_id}/places]
Collection of places of user with id `user_id`
<!---
+ Parameters
    + user_id (required, number, `1`) ... Numeric `user_id` of the Place to perform action with. Has example value.
--->

    

### Send place to user [POST]

+ Request (application/json)

        { 
          "title": "Car parking",
          "latitude": 40.1236,
          "longitude": 14.3281,
          "icon": "car",
          "date": "2015-03-11 14:09"
        }
    
+ Response 201 

# Group Places
Places related resources of the **Places API**

## Places Collection [/places]
### List all user's Places [GET]

+ Request

    + Header
    
            Authorization: Basic NTUzNjYxODJlNGIwNWI0Yjk5YjI3YjQ5Og==

+ Response 200 (application/json)

        [{
          "title": "Cycle parking",
          "latitude": 43.1256,
          "longitude": 12.5314,
          "altitude": 12,
          "icon": "cycle",
          "date": "2015-03-11 12:57"
        },
        {
          "title": "Hotel",
          "latitude": 42.1256,
          "longitude": 12.5214,
          "altitude": 15,
          "icon": "house",
          "date": "2015-03-10 10:07"
        }]

### Create a Place [POST]
+ title (string) - Title of the place
+ latitude (decimal) - Latitude of the place.
+ longitude (decimal) - Longitude of the place.
+ altitude (decimal) - Altitude of the place.
+ icon (string) - Name of the icon of the string.
+ date (date) - Creation date


+ Request (application/json)

    + Header
    
            Authorization: Basic NTUzNjYxODJlNGIwNWI0Yjk5YjI3YjQ5Og==
            
    + Body

            {
              "title": "Vienna sousages",
              "latitude": 40.1236,
              "longitude": 14.3281,
              "altitude": 15,
              "icon": "food",
              "date": "2015-03-11T14:09:00.000Z"
            }

+ Response 201 (application/json)

    + Header

            Location: /places/3

    + Body 
            

            {
              "title": "Vienna sousages",
              "latitude": 40.1236,
              "longitude": 14.3281,
              "icon": "food"
              "date": "2015-03-11 14:09"
            }
        


## Place [/places/{place_id}]
A single Place object with all its details

+ Parameters
    + place_id (required, number, `0`) ... Numeric `place-id` of the Place to perform action with. Has example value.

### Retrieve a Place [GET]

+ Request

    + Header
    
            Authorization: Basic NTUzNjYxODJlNGIwNWI0Yjk5YjI3YjQ5Og==
      
+ Response 200 (application/json)

        {
          "title": "Cycle parking",
          "latitude": 43.1256,
          "longitude": 12.5314,
          "altitude": 15,
          "icon": "cycle"
          "date": "2015-03-11 12:57"
        }

### Remove a Place [DELETE]

+ Request (application/json)

    + Header
    
            Authorization: Basic NTUzNjYxODJlNGIwNWI0Yjk5YjI3YjQ5Og==

+ Response 200 (application/json)

        {
          "title": "Car parking",
          "latitude": 40.1236,
          "longitude": 14.3281,
          "icon": "car"
          "date": "2015-03-11 14:09"
        }

### Update a Place [PUT]



+ Request (application/json)

    + Header
    
            Authorization: Basic NTUzNjYxODJlNGIwNWI0Yjk5YjI3YjQ5Og==
    + Body

            {
              "title": "Car parking",
              "latitude": 40.1236,
              "longitude": 14.3281,
              "altitude": 15,
              "icon": "car",
              "date": "2015-03-11T14:09:00.000Z"
            }

+ Response 200 (application/json)

        {
          "title": "Car parking",
          "latitude": 40.1236,
          "longitude": 14.3281,
          "icon": "car"
          "date": "2015-03-11 14:09"
        }

+ Response 201 (application/json)

    + Header

            Location: /places/1

    + Body 

            {
              "title": "Car parking",
              "latitude": 40.1236,
              "longitude": 14.3281,
              "icon": "car"
              "date": "2015-03-11 14:09"
            }
            

