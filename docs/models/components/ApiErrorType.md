# ApiErrorType

High-level error category.

## Example Usage

```java
import net.nova.api.models.components.ApiErrorType;

ApiErrorType value = ApiErrorType.AUTHENTICATION_ERROR;

// Open enum: use .of() to create instances from custom string values
ApiErrorType custom = ApiErrorType.of("custom_value");
```


## Values

| Name                    | Value                   |
| ----------------------- | ----------------------- |
| `AUTHENTICATION_ERROR`  | authentication_error    |
| `PERMISSION_ERROR`      | permission_error        |
| `INVALID_REQUEST_ERROR` | invalid_request_error   |
| `NOT_FOUND_ERROR`       | not_found_error         |
| `CONFLICT_ERROR`        | conflict_error          |
| `RATE_LIMIT_ERROR`      | rate_limit_error        |
| `API_ERROR`             | api_error               |