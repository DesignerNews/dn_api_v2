## Jobs

Jobs resources are the jobs currently listed on the [Designer News jobs board](https://designernews.co/jobs).

### Available actions

```
GET /api/v2/jobs
GET /api/v2/jobs/:id
```

### Attributes

- `organization_name`: {String} The organization running the job listing, e.g. "LayerVault".
- `location`: {String} The location where the job is located, e.g. "New York, NY".
- `url`: {String} The URL for the job listing itself.
- `title`: {String} The title for job listing, e.g. "UX Designer".
