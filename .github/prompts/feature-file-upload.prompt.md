---
description: 'Add streaming file upload/download with size, type and path safety'
agent: agent
argument-hint: '[what file, for which resource]'
---
<!-- 030 | C. Feature development | build -->
# 030 · File upload and download

Act as a senior Spring Boot engineer with a security mindset.

## Context
- Purpose: [PURPOSE]; storage: [STORAGE, e.g. S3, file system, database]
- Limits: [MAX_SIZE], allowed types: [ALLOWED_TYPES]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Implement upload and download without holding whole files in memory or trusting client input.

## Constraints
- Stream; never read the whole file into a byte array. Generate storage names server-side.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- File too large; wrong or spoofed content type; empty file; duplicate upload.
- Filename with path traversal or unusual characters.
- Storage failure mid-upload; metadata row saved but file missing, and the reverse.
- Download by a user who does not own the file.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- Tests for each case; correct Content-Type, Content-Disposition and status codes.
