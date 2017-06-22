# Campgrounds

## Search Campgrounds

```ruby
# models/api_client/campground.rb
require 'her'

module ApiClient
  class Campground
    include Her::Model
  end
end


# controllers/api_client/campgrounds_controller.rb
require_dependency 'api_client/campground'

module ApiClient
  class CampgroundsController < ApplicationController
    def find_campground
      @campground = ::ApiClient::Campground.search('Austin TX USA')
    end
  end
end
```

```shell
CONTENT_TYPE=application/json
HOST=https://www.roverpass.com
URI=/api/campgrounds/search/Austin%20Texas%20USA
API_TOKEN=super_secret_token # Not actual API_TOKEN. Don't use this.
curl -H "Accept:$CONTENT_TYPE" -H "Content-Type:$CONTENT_TYPE" -H "Authorization: Token token=$API_TOKEN" "$HOST$URI"
```

This endpoint allows the client to pass in a query to geolocate campgrounds within a 40 mile radius.

### HTTP Request

`GET http://www.roverpass.com/api/campgrounds/search/:query`

### Ruby/Her

If you'd like to use a Ruby integration, our API works seamlessly with the [Her](https://github.com/remiprev/her) gem.

> A successful response will be a JSON array similar to this:

```json
[
  {
    "slug": "roverpass-funland",
    "name": "RoverPass Funland Campground",
    "phone": "314274-3624",
    "ranking_score": 474,
    "latitude": 30.272920551044,
    "longitude": -97.744463633061,
    "full_address": "3101 Bee Caves Rd, Austin, Texas, 78746",
    "address": "3101 Bee Caves Rd",
    "address2": null,
    "city_name": "Austin",
    "state_name": "Texas",
    "zip": "78746",
    "bio": "Hey, fellow RVers! We're excited to show you what we've built. Fill out the reservation request box on the right. You'll be able to save your rig details and see how easy it is to fire one off!",
    "official_description": "This is a wonderful campground that has a lot of fun to offer at a really affordable price. It\u2019s located on 3101 Bee Caves Rd in Austin, TX. This is a wonderful location as it\u2019s close to a lot of great attractions, restaurants, and many places to shop at. There are plenty of sites to choose from that has a wide range of amenities. These include, but not limited to: electricity, fire pit, laundry facilities, showers, and clean water. \r\n\r\nThere are a plethora of activities to do here like basketball, kite-Boarding, historic sightseeing, shuffleboard, wake-boarding, and more. From all the things you can do and see here it is overall not only fun but a very relaxing and calming place to stay for the night, or longer. If you are in this area check out this wondrous park as it has a lot here for a great price.",
    "average_review_rating": 4.5,
    "information_verified": false,
    "picture_url": "https:\/\/s3-us-west-2.amazonaws.com\/cdn.roverpass.com\/marketing-photos\/default-campground-list-image.png",
    "amenities": [
      {
        "name": "Community Showers"
      },
      {
        "name": "Community Fire Pit"
      },
      {
        "name": "Big Rig Friendly"
      },
      {
        "name": "30 Amps"
      },
      {
        "name": "100 Amps"
      },
      {
        "name": "Community Restrooms"
      },
      {
        "name": "Community BBQ\/Grill"
      },
      {
        "name": "20 Amps"
      },
      {
        "name": "50 Amps"
      },
      {
        "name": "General Store"
      },
      {
        "name": "Trash Service"
      },
      {
        "name": "Fitness Room"
      },
      {
        "name": "Propane Refilling Station"
      },
      {
        "name": "Laundry Facilities"
      },
      {
        "name": "ADA Accessible"
      },
      {
        "name": "Pet Friendly"
      },
      {
        "name": "Waterfront"
      },
      {
        "name": "Clubhouse"
      },
      {
        "name": "Community Water Fountain"
      },
      {
        "name": "Paved Roads"
      }
    ],
    "reviews": [
      {
        "content": "Testing the reviews.",
        "rating": "5.0"
      },
      {
        "content": "RoverPass is on a mission to make it super easy to find a campground or RV park and book online, cutting out the phone calls or waiting to hear back from the campground. Every day we're working hard to make the experience even better. Let us know what you think!",
        "rating": "5.0"
      },
      {
        "content": "RoverPass is the best campground reservation company out there.  They make is so easy to book a park! ",
        "rating": "3.0"
      },
      {
        "content": "This name of this place is very fitting! It sure it a funland! The staff is so welcoming and warm that we felt like family. There were a plethora of sites to choose from that were very spacious and had all the amenities we could ask for. There were a ton of fun and relaxing activities to choose from as well. The location was great as it was easy to get to and there was not only so much inside the park but there was a lot of great attractions, places to eat and shop that was only a short drive away. Overall a great place for a great price!  - Review provided by RV Park Recommendations & Reviews Facebook Group",
        "rating": "5.0"
      }
    ],
    "widget_url": null
  }
]
```

### Query Parameters

Parameter | Description | Required? | Example | Type
--------- | ----------- | --------- | ------- | ----
query | Encoded Search Query, preferrably from Google Places Autocomplete | Yes | Austin%20TX%20USA | String
page | This changes the page of the pagination of results | false | 1 | Integer
per_page | This changes the amount of results on each page of the pagination | false | 10 | Integer

## Get a Specific Campground

```ruby
# models/api_client/campground.rb
require 'her'

module ApiClient
  class Campground
    include Her::Model
  end
end


# controllers/api_client/campgrounds_controller.rb
require_dependency 'api_client/campground'

module ApiClient
  class CampgroundsController < ApplicationController
    def find_campground
      @campground = ::ApiClient::Campground.find('roverpass-funland')
    end
  end
end
```

```shell
CONTENT_TYPE=application/json
HOST=https://www.roverpass.com
URI=/api/campgrounds/:slug
API_TOKEN=super_secret_token # Not actual API_TOKEN. Don't use this.
curl -H "Accept:$CONTENT_TYPE" -H "Content-Type:$CONTENT_TYPE" -H "Authorization: Token token=$API_TOKEN" "$HOST$URI"
```

This endpoint allows the client to pass in an `:slug` or `:id` to receive a specific campground.

### HTTP Request

`GET http://www.roverpass.com/api/campgrounds/:slug`

### Ruby/Her

If you'd like to use a Ruby integration, our API works seamlessly with the [Her](https://github.com/remiprev/her) gem.

> The above command returns JSON structured like this:

```json
{
  "slug": "roverpass-funland",
  "name": "RoverPass Funland Campground",
  "phone": "314274-3624",
  "ranking_score": 474,
  "latitude": 30.272920551044,
  "longitude": -97.744463633061,
  "full_address": "3101 Bee Caves Rd, Austin, Texas, 78746",
  "address": "3101 Bee Caves Rd",
  "address2": null,
  "city_name": "Austin",
  "state_name": "Texas",
  "zip": "78746",
  "bio": "Hey, fellow RVers! We're excited to show you what we've built. Fill out the reservation request box on the right. You'll be able to save your rig details and see how easy it is to fire one off!",
  "official_description": "This is a wonderful campground that has a lot of fun to offer at a really affordable price. It\u2019s located on 3101 Bee Caves Rd in Austin, TX. This is a wonderful location as it\u2019s close to a lot of great attractions, restaurants, and many places to shop at. There are plenty of sites to choose from that has a wide range of amenities. These include, but not limited to: electricity, fire pit, laundry facilities, showers, and clean water. \r\n\r\nThere are a plethora of activities to do here like basketball, kite-Boarding, historic sightseeing, shuffleboard, wake-boarding, and more. From all the things you can do and see here it is overall not only fun but a very relaxing and calming place to stay for the night, or longer. If you are in this area check out this wondrous park as it has a lot here for a great price.",
  "average_review_rating": 4.5,
  "information_verified": false,
  "picture_url": "https:\/\/s3-us-west-2.amazonaws.com\/cdn.roverpass.com\/marketing-photos\/default-campground-list-image.png",
  "amenities": [
    {
      "name": "Community Showers"
    },
    {
      "name": "Community Fire Pit"
    },
    {
      "name": "Big Rig Friendly"
    },
    {
      "name": "30 Amps"
    },
    {
      "name": "100 Amps"
    },
    {
      "name": "Community Restrooms"
    },
    {
      "name": "Community BBQ\/Grill"
    },
    {
      "name": "20 Amps"
    },
    {
      "name": "50 Amps"
    },
    {
      "name": "General Store"
    },
    {
      "name": "Trash Service"
    },
    {
      "name": "Fitness Room"
    },
    {
      "name": "Propane Refilling Station"
    },
    {
      "name": "Laundry Facilities"
    },
    {
      "name": "ADA Accessible"
    },
    {
      "name": "Pet Friendly"
    },
    {
      "name": "Waterfront"
    },
    {
      "name": "Clubhouse"
    },
    {
      "name": "Community Water Fountain"
    },
    {
      "name": "Paved Roads"
    }
  ],
  "reviews": [
    {
      "content": "Testing the reviews.",
      "rating": "5.0"
    },
    {
      "content": "RoverPass is on a mission to make it super easy to find a campground or RV park and book online, cutting out the phone calls or waiting to hear back from the campground. Every day we're working hard to make the experience even better. Let us know what you think!",
      "rating": "5.0"
    },
    {
      "content": "RoverPass is the best campground reservation company out there.  They make is so easy to book a park! ",
      "rating": "3.0"
    },
    {
      "content": "This name of this place is very fitting! It sure it a funland! The staff is so welcoming and warm that we felt like family. There were a plethora of sites to choose from that were very spacious and had all the amenities we could ask for. There were a ton of fun and relaxing activities to choose from as well. The location was great as it was easy to get to and there was not only so much inside the park but there was a lot of great attractions, places to eat and shop that was only a short drive away. Overall a great place for a great price!  - Review provided by RV Park Recommendations & Reviews Facebook Group",
      "rating": "5.0"
    }
  ],
  "widget_url": null
}
```

### Query Parameters

Parameter | Description | Required? | Example | Type
--------- | ----------- | --------- | ------- | ----
slug | Specific identifier for each campground | Yes | 'roverpass-funland'  | String
