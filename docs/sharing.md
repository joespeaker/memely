# Sharing and Embed Integration

## Per-image sharing payload

`GET /images/{id}/share` should return:
- Direct canonical image URL
- Download URL
- Clipboard-safe permalink
- Mobile share-sheet title/text/url

## Social formatting

Each image page should expose:
- Open Graph title/description/image
- Twitter/X summary card tags
- Preview image using 1080px or best-fit variant

## Embed snippets

Provide generated snippets:
- iFrame embed
- Read-only image+attribution HTML block
