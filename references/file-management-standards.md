# File Management Standards

## General

Treat every uploaded file as untrusted. Implement upload handling centrally and reuse it across modules.

## Validation

Validate:
- Upload error status.
- File size.
- Extension against an explicit allowlist.
- Actual MIME type using `finfo`.
- Expected extension/MIME combinations.
- Image dimensions where relevant.
- User permission and business rules.

Do not trust the browser's `Content-Type`, filename, or extension alone. MIME checks do not guarantee that a file is harmless; use malware scanning where the deployment requires and supports it.

## Storage

Generate random server-side filenames. Do not use user-provided paths. Store private documents outside the public web root where practical. Prevent script execution in upload directories. Apply restrictive filesystem permissions. Keep metadata in the database.

## Downloads

Serve private files through an authenticated download endpoint. Check record-level permission before returning the file. Resolve paths from trusted database metadata and a fixed storage root. Prevent path traversal. Set appropriate content headers and avoid exposing physical server paths.

## Images

Where image processing is required, use a maintained image library or safe native capabilities. Re-encode images when appropriate. Do not assume that a file is a valid image merely because its extension says so.

## Deletion and replacement

Validate ownership and permission before deletion. Avoid deleting an existing valid file until its replacement has passed validation and has been stored successfully. Handle orphaned files through a documented cleanup process.

## Security checklist

No executable uploads; random filenames; MIME and extension validation; size limits; protected storage; authorised downloads; path traversal protection; safe logging; and appropriate malware scanning where required.
