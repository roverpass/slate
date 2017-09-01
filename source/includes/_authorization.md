# Configuration

## Authorization Tokens

```shell
API_TOKEN=supersecrettoken # Not actual API_TOKEN. Don't use this.
CONTENT_TYPE=application/json
VERSION=1
HOST=https://www.roverpass.com
URI=/api/partner
curl -H "Accept:$CONTENT_TYPE" -H "Version=$VERSION" -H "Authorization: Token token=$API_TOKEN" "$HOST$URI"
```

In order to use the Roverpass API, you will first need to be given an API_TOKEN. Once received, you will need to pass in your API_TOKEN as a header in each request, like this:

`-H "Authorization: Token token=$API_TOKEN"`

This will allow us to verify who is receiving each response.

Each API Token in the RoverPass database will correspond to a `Partner`. We have set up an endpoint so that you can ensure your API Token corresponds to you as a partner. Your partner name will be lowercase with no spaces. For example, if your partner name was `RoverPass`, the response would look like:

`{"partner": "roverpass"}`

## Response Types

```shell
API_TOKEN=supersecrettoken
CONTENT_TYPE=application/vnd.api+json
VERSION=1
HOST=https://www.roverpass.com
URI=/api/campgrounds/roverpass-funland-campground-austin-tx
curl -H "Accept:$CONTENT_TYPE" -H "Version=$VERSION" -H "Authorization: Token token=$API_TOKEN" "$HOST$URI"
```

The type of response you would like to receive is also necessary. We accept two types:

If you would like to receive a response as simple attributes, use this header:

`-H "Accept:application/json"`

If you would like to receive a response structured with the [JSON:API specification](http://jsonapi.org/), use this header:

`-H "Accept:application/vnd.api+json"`

## Versions

```shell
API_TOKEN=supersecrettoken
CONTENT_TYPE=application/json
VERSION=1
HOST=https://www.roverpass.com
URI=/api/partner
curl -H "Accept:$CONTENT_TYPE" -H "Version=$VERSION" -H "Authorization: Token token=$API_TOKEN" "$HOST$URI"
```

While adding a version number to the header is not required (the current default is 1), we HIGHLY RECOMMEND adding a version header like this:

`-H "Version=1"`

Our API is only on version 1, but as we update, it is likely later versions will be set the default, and as conventions and specifications in the industry change, so will our API functionality. Adding a version will greatly reduce future errors.
