# Authentication

In order to use the Roverpass API, you will first need to be given an API_TOKEN. Once received, you will need to pass in your API_TOKEN as a header in each request, like so:

`-H "Authorization: Token token=$API_TOKEN"`

This will allow us to verify who is receiving each response.

Application type is not necessary, but if you are a perfectionist, you can pass in `application/json` like this:

`-H "Accept:application/json" -H "Content-Type:application/json"`

```shell
CONTENT_TYPE=application/json
HOST=https://www.roverpass.com
URI=/api/campgrounds/roverpass-funland-campground-austin-tx
API_TOKEN=sup3rs3cr3tp@55w0rd # Not actual API_TOKEN. Don't use this.
curl -H "Accept:$CONTENT_TYPE" -H "Content-Type:$CONTENT_TYPE" -H "Authorization: Token token=$API_TOKEN" "$HOST$URI"
```
