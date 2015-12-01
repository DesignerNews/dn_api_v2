## Resources

### Retrieving a Single Resource

Single resources can be queried using a simple and predictable interface. It follows the following format:

```
GET /api/v2/{plural_resource_name}/:id
```

With this format, you can retrieve a single resource. Let's get the first user model:

```shell
$ curl https://www.designernews.co/api/v2/users/1
```

You will then get the following response:

```json
{
  "users": [{
    "id": "1",
    "href": "https://api.designernews.co/api/v2/users/1",
    "links": {
      "comments": ["2", "7", "12"],
      "stories": ["1", "20"],
      "upvotes": [],
      "downvotes": []
    },
    "first_name": "Kelly",
    "karma": 2438,
    "last_name": "Sutton"
  }]
}
```

This response is a subset of the actual response for this request.

### Retrieving Multiple Resources

Multiple responses can be retieved at once by using a comma delimited set of IDs:

```
GET /api/v2/{plural_resource_name}/:id1,:id2,:id3
```

Let’s see how that works with the users resource.

```shell
$ curl https://www.designernews.co/api/v2/users/1,2,3
```

That results in a response with the users identified by the IDs 1, 2, and 3.

```json
{
  "users": [{
    "id": "1"
  },
  {
    "id": "2"
  },
  {
    "id": "3"
  }]
}
```

Note again: this a subset of the actual response.

### Creating a Resource

Resources can be created by issuing a `POST` request to the appropriate endpoint with an authenticated user.

All creation requests take the following format:

```
POST /api/v2/{plural_resource_name}
```

Let’s see how that looks when creating a story.

```shell
$ curl -X POST \
  -H 'Authorization: Bearer <your access token>' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{ "stories": { "title": "Bring in the Cats", "url": "http://bringinthecats.com/", "links": { "user": "1" } } }' \
  https://www.designernews.co/api/v2/stories
```

This request will create a story resource with the title "Bring in the Cats" with the URL "http://bringinthecats.com/" with the user with the ID of "1" as its author. If things go over
well, you'll receive a `HTTP 201 Created` response with the newly created resource in the response body.

### Updating a Resource

Updating resources is done with a well-formed `PUT` request to the appropriate endpoint with an authenticated user.

All updated requests take the following format:

```
PUT /api/v2/{plural_resource_name}/:id
```

Let's see how that would look updating the `title` attribute of the story with the ID `1`.

```shell
$ curl -X PUT \
  -H 'Authorization: Bearer <your access token>' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{ "stories": { "title": "Bring in the cats.biz" }' \
  https://www.designernews.co/api/v2/stories/1
```

This request updates the `title` attribute of the story with the ID of `1` to be "Bring in the cats.biz".
If all goes well, you'll receive a `HTTP 200 OK` response with the newly-updated resource.

### Deleting a Resource

Deleting resources is simple. Just issue a `DELETE` request to the appropriate endpoint with an
authenticated user.

```
DELETE /api/v2/{plural_resource_name}/:id
```

Let’s see how that would look deleting the story with the ID of `1`.

```shell
$ curl -X DELETE https://www.designernews.co/api/v2/stories/1
```

If things go well, you will receive an `HTTP 204 No Content` response. Please bear in mind, you
will not be able to delete resources you are not the owner of.
