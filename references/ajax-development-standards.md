# AJAX Development Standards

## Appropriate use

Use AJAX where it improves interaction, such as dependent dropdowns, asynchronous form submission, modal workflows, search suggestions, and status updates.

Do not use jQuery or DataTables for database table pagination, filtering, or sorting. Those operations remain server-side.

## Endpoint requirements

Every endpoint must independently:
- Validate the HTTP method.
- Authenticate the user where required.
- Check permissions and record-level access.
- Verify CSRF tokens for state-changing requests.
- Validate and normalise input.
- Apply safe database query handling.
- Return a consistent response.
- Avoid exposing SQL errors, stack traces, paths, or secrets.

## Response format

Use a predictable JSON structure, for example:

```json
{
  "success": true,
  "message": "Record saved successfully.",
  "data": {}
}
```

For failures, return `success: false` and a safe message. Use suitable HTTP status codes. Do not include internal exception details in public responses.

## Frontend

Use jQuery only where appropriate and follow the existing project's JavaScript conventions. Handle loading, success, validation errors, network failures, and duplicate submissions. Do not assume the browser response is trustworthy.

## File uploads

Use `FormData` where appropriate. Apply the same upload validation and storage rules as ordinary form submissions. Never trust client-provided filenames or MIME types.
