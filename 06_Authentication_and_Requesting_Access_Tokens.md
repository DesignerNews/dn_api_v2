## Authentication and Requesting Access Tokens

Requests that modify, create, or destroy resources require authentication. Requests that only read resources do not.

The easiest way to authenticate a user is to use the `grant_type="password"` parameter when requesting
an OAuth token:


```shell
curl -i https://www.designernews.co/oauth/token \
  -F grant_type="password" \
  -F username="<your Designer News username>" \
  -F password="<your Designer News password>"
```

Which will return an Access token response like this one:

```json
{
  "access_token":"aec9c670cf5e673bfedf83d055d2a2e0e5f37e52d3b41cffcf7874f73a7458bf",
  "token_type":"bearer",
  "scope":"user"
}
```

The access token must be then passed in the Authorization header for all requests that attempt to modify a resource. See examples below for more information.
