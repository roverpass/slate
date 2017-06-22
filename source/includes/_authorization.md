# Authentication

> To authorize, use this code:

```ruby
require 'roverpass'

api = Roverpass::APIClient.authorize!('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

Roverpass uses API keys to allow access to the API. You can register a new Roverpass API key at our [developer portal](http://example.com/developers).

Roverpass expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>
