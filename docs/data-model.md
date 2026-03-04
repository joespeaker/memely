# Data Model Notes

Core entities are implemented in `apps/api/migrations/001_initial.sql`.

## Relationship summary

- `users` 1:N `images`
- `images` 1:N `image_variants`
- `images` N:M `tags` through `image_tags`
- `images` 1:N `reports`
- `images` 1:N `moderation_logs`
- `users` N:M `images` through `favorites`
- `images` 1:N `trending_metrics`

## Image object requirements mapping

`images` includes:
- UUID id
- original file URL
- aspect ratio
- transparent flag
- OCR text
- manual tags
- AI tags
- upload source
- license type
- moderation/status

`image_variants` stores generated small/medium/full derivatives and metadata.
