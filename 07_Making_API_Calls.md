## Making API Calls

Making API calls is simple, and can be tested out using CURL. For authenticated requests,
don’t forget to include your Authorization header:

```shell
curl -H 'Authorization: Bearer <your access token>' \
  'https://www.designernews.co/api/v2/me'
```

