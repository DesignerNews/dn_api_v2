## Votes

The fuel that keeps Designer News running are the votes. Votes determine the popularity
of a story, comment, or MOTD.

There are the following vote types:

- {Upvote} - An upvote on a story
- {Downvote} - A downvote on a story
- {MotdUpvote} - An upvote on an MOTD
- {MotdDownvote} - A downvote on an MOTD
- {CommentUpvote} - An upvote on a comment
- {CommentDownvote} - A downvote on a comment

When building URLs, we use the standard “underscoring” method found in most programming languages or web
frameworks. Thus, our voting resources are located at the following URLs:

```
/api/v2/upvotes
/api/v2/downvotes
/api/v2/motd_upvotes
/api/v2/motd_downvotes
/api/v2/comment_upvotes
/api/v2/comment_downvotes
```

### Available actions

Here, the `{vote_type}` should be replaced with the type of vote resource you wish to interact with.

```
GET /api/v2/{vote_type}/:id
POST /api/v2/{vote_type}
DELETE /api/v2/{vote_type}
```

### Linked resources

- `user`: {User} The user ID performing the voting action
- target resource: {Comment}, {Story}, or {Motd}. The ID of the target resource. This key will either be `comment`, `story`, or `motd`


### Creating a vote

To create a vote, you must include both the user and the target resource in the `links` section of the payload.
For example, here is how we would create an upvote as a user with the ID of `1` upvoting a story with a
an ID of `101`.

```shell
curl -X POST \
  -H "Authorization: Bearer <your_auth_token>" \
  -H "Content-Type: application/vnd.api+json" \
  -d '{ "upvotes": { "links": { "story": "101", "user": "1" } } }' \
  https://www.designernews.co/api/v2/upvotes
```
