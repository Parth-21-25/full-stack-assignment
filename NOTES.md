# Notes

## Summary of Changes

* Fixed the backend status filter by correcting SQL operator precedence, ensuring archived tasks are excluded and the selected status is applied correctly.
* Removed a query-dependent `Thread.sleep()` that unnecessarily delayed API responses.
* Added backend validation for `page` and `pageSize` to return `400 Bad Request` for invalid values instead of `500 Internal Server Error`.
* Reset pagination to page 1 whenever the search query or status filter changes.
* Fixed frontend error handling so loading state is cleared and previous errors are reset when requests fail or recover.
* Fixed the same SQL operator-precedence issue in the H2 and Oracle reference queries to keep their logic consistent with the application.

## What I Chose Not to Change

I avoided broad UI, architectural, or feature changes because the assignment asked us to focus on the highest-value issues.
I also did not change pagination behavior for unusually large page sizes because the existing application does not specify a maximum.
I also did not introduce service layer as application works fine without it. but for a larger application I would consider adding a Service layer for better code maintainability.

## Biggest Remaining Risk

The API still has limited centralized input validation and exception handling. 
For example, an unsupported status value can still result in a generic `500 Internal Server Error` rather than a structured `400 Bad Request`.
Centralized exception handling and clearer API error responses would improve robustness.

## Tools / AI Used

I used IntelliJ IDEA for Spring Boot, VS Code for React, Git for version control,Postman and Chrome browser for API testing, and the H2 console for database inspection.

I used Claude as a debugging and coding assistant to understand the existing code, reason about API/UI behavior, identify root causes, and suggest focused fixes. 
I also used it mainly for syntax-related help, including SQL/Oracle query syntax and implementation details. I applied and tested the changes myself.
