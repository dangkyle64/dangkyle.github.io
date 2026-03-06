# read-book-api

## Testing 
Currently writing...

## Implement Automated Testing (CI)
Currently writing...

## Configure Safe Deployment Workflow (CD)
Currently writing...

## Rate Limiting
Currently writing...

## Why RESTful?
- Endpoints are resource-based, providing a standardized way to interact with each resource using HTTP methods. `/books`, `/books/:id`
- Standard HTTP methods map to CRUD operations `GET`, `POST`, `PUT`, `PATCH`, `DELETE`
- JSON responses allow for stateless communication
- Designed for clarity and simplicity for an entry-level API

## Using Try/Catch More Effectively

Early on, I wrapped entire functions in try/catch, but realized that it’s best to use it only around code that can throw unpredictable runtime errors—like file reading, JSON parsing, or database operations.

For expected business logic issues, such as “book not found” or invalid input, it’s better to manually check and throw meaningful errors. This keeps error handling clear, avoids masking real problems, and makes API responses predictable for clients.

[⬅ Back](../)
---
Last updated: 2026-03-03