---
layout: default
title: HTTParty
parent: Ruby
---

# HTTParty Cheatsheet

---

Requests

```rb
headers = {
  "X-API-KEY" => "#{api_key}",
  "Content-Type" => "application/json",
  "Authorization" => "Bearer #{access_token}"
}

basic_auth = {
  username: ENV['BASIC_AUTH_USERNAME'],
  password: ENV['BASIC_AUTH_PASSWORD']
}

payload = {
  foo: 'bar'
}

# GET requests
HTTParty.get('https://example.com/api/products', headers: headers)
# The following 2 requests are equivalent
HTTParty.get('https://example.com/api/products', query: {foo: 'bar'})
HTTParty.get('https://example.com/api/products?foo=bar')

# POST requets
HTTParty.post('http://foo.com/resources', body: {foo: 'bar'})
HTTParty.post('https://example.com/api/products', query: {foo: 'bar'})
options = {
  body: payload.to_json,
  basic_auth: basic_auth
}
HTTParty.post('https://example.com/api/products', options)
```

Responses

```rb
response = HTTParty.post('https://example.com/api/products', options)
#=> {"success"=>true}

response.headers
#=> {...}
response.request
#=> HTTParty::Request object

# Raw response body
response.body
#=> "{\"success\":true}"

# HTTP status check
response.code
#=> 200
response.message
#=> "OK"
response.ok?
#=> true
response.not_found?
#=> false
```
