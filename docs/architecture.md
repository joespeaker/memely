# Memely Architecture (v1)

## System boundaries

- **API service**: auth, search, upload intake, sharing, moderation/admin, DMCA intake.
- **Worker service**: async image processing, OCR extraction, tag generation, trending aggregation.
- **Storage/CDN**: original + variants persisted in object storage and distributed via CDN.
- **Database**: PostgreSQL for transactional entities and moderation/compliance records.

## Request flows

1. **Upload**: Authenticated user uploads image → API validates file type/size/license confirmation → image record created as `pending_review` → processing job queued.
2. **Processing**: Worker generates 256/512/1080 variants, strips metadata, computes placeholder/blurhash, writes `image_variants` and updates image metadata.
3. **Moderation**: Admin approves/rejects; actions captured in `moderation_logs`.
4. **Search**: Client calls `/search`; API ranks by text relevance + trending boost.

## Scalability model

- Stateless API nodes scale horizontally behind a load balancer.
- Queue-backed workers scale independently by concurrency class.
- CDN offloads asset delivery from API.

## Security model

- JWT/session auth for users.
- Admin role separation for moderation endpoints.
- Rate limiting + CSRF + upload scanning hooks on intake routes.

## Performance targets

- Search p95 < 300ms.
- CDN TTFB < 150ms for cached image variants.
- API responses optimized for lightweight keyboard/mobile clients.
