# Authentication

## Header

In order to use the Roverpass API, you will first need to be given an API_TOKEN. Once received, you will need to pass in your API_TOKEN as a header in each request, like this:

`-H "Authorization: Token token=$API_TOKEN"`

This will allow us to verify who is receiving each response.

Application type is not necessary, but if you are a perfectionist, you can pass in `application/json` like this:

`-H "Accept:application/json" -H "Content-Type:application/json"`

```shell
API_TOKEN=supersecrettoken # Not actual API_TOKEN. Don't use this.
CONTENT_TYPE=application/json
HOST=https://www.roverpass.com
URI=/api/campgrounds/roverpass-funland-campground-austin-tx
curl -H "Accept:$CONTENT_TYPE" -H "Content-Type:$CONTENT_TYPE" -H "Authorization: Token token=$API_TOKEN" "$HOST$URI"
```

## Partners

Each API Token in the RoverPass database will correspond to a `Partner`. We have set up an endpoint so that you can ensure your API Token corresponds to you as a partner. Your partner name will be lowercase with no spaces. For example, if your partner name was `RoverPass`, the response would look like:

`{"partner": "roverpass"}`

```shell
API_TOKEN=supersecrettoken
CONTENT_TYPE=application/json
HOST=https://www.roverpass.com
URI=/api/partner
curl -H "Accept:$CONTENT_TYPE" -H "Content-Type:$CONTENT_TYPE" -H "Authorization: Token token=$API_TOKEN" "$HOST$URI"
```
