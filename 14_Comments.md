## Comments

### Available actions

```
GET /api/v2/comments/:id
PUT /api/v2/comments/:id
POST /api/v2/comments
DELETE /api/v2/comments/:id
```

### Attributes

- `body`: {String} The body of the comment, in Markdown.

### Editable attributes

- `body`

### Linked resources

- `comments`: {Comment} The replies on the current comment.
- `comment_upvotes`: {CommentUpvote} The upvotes on the current comment.
- `comment_downvotes`: {CommentDownvote} The downvotes on the current comment.
- `parent_comment`: {Comment} The comment this comment is attach to. Either this or `story` will be present.
- `story`: {Story} The story this comment is attached to.
- `user`: {User} The user that left this comment

### Posting a comment

Here's how we would post a comment for a story with ID `101` as a user with ID `1`

```
curl -X POST \ 
-H "Authorization: Bearer <your_auth_token>" \
-H "Content-Type: application/vnd.api+json" \
-d '{"comments":{"comment":{"body": "First story message"},"links":{"story":"101","user":"1"}}}'\
https://www.designernews.co/api/v2/comments/
```

Here's how we would post a reply for a comment with ID `123` as a user with ID `1`

```
curl -X POST \
-H "Authorization: Bearer <your_auth_token>" \
-H "Content-Type: application/vnd.api+json" \
-d '{"comments":{"comment":{"body": "First message"},"links":{"parent_comment":"123","user":"1"}}}' \
https://www.designernews.co/api/v2/comments/
```
