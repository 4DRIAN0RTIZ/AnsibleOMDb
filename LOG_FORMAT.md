# Log Format Documentation

## Overview

Logs are saved to `ansible_api_excel.log` in structured format for easy parsing.

## Format Structure

```
[<ISO8601_timestamp>][<LEVEL>] - <error_type> : <additional_context>
```

**Components:**
- **timestamp**: ISO8601 format (e.g., `[2026-01-08T16:05:22Z]`)
- **level**: `[INFO]` or `[ERROR]`
- **error_type**: Identifier in snake_case
- **additional_context**: Key-value pairs with details

## Error Types

| Type | Level | Description |
|------|-------|-------------|
| `host_unreachable` | ERROR | Connection timeout |
| `host_reachable` | INFO | Host online |
| `api_call_failed` | ERROR | API request failed |
| `api_call_success` | INFO | API request successful |
| `api_no_results` | ERROR | No results returned |
| `excel_created` | INFO | File created successfully |
| `excel_creation_failed` | ERROR | File creation failed |
| `execution_complete` | INFO | Operation completed |
| `execution_success` | INFO | Execution successful |
| `execution_failed` | ERROR | Execution failed |


## Example Log Entries

```
[2026-01-08T16:01:31Z][ERROR] - host_unreachable : host=10.100.1.121 Connection timeout
[2026-01-08T16:05:22Z][INFO] - host_reachable : host=10.100.1.100 Host is online
[2026-01-08T16:05:25Z][INFO] - api_call_success : host=10.100.1.100 search_term=Matrix results_count=10
[2026-01-08T16:05:28Z][INFO] - excel_created : host=10.100.1.100 output_file=movies_results.xlsx movies_count=10
[2026-01-08T16:05:30Z][INFO] - execution_success : host=10.100.1.100 status=SUCCESS
```
