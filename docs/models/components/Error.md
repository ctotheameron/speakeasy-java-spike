# Error

Machine-readable OAuth error code (RFC 6749 §5.2).

## Example Usage

```java
import net.nova.api.models.components.Error;

Error value = Error.INVALID_REQUEST;

// Open enum: use .of() to create instances from custom string values
Error custom = Error.of("custom_value");
```


## Values

| Name                     | Value                    |
| ------------------------ | ------------------------ |
| `INVALID_REQUEST`        | invalid_request          |
| `INVALID_CLIENT`         | invalid_client           |
| `INVALID_GRANT`          | invalid_grant            |
| `UNAUTHORIZED_CLIENT`    | unauthorized_client      |
| `UNSUPPORTED_GRANT_TYPE` | unsupported_grant_type   |
| `INVALID_SCOPE`          | invalid_scope            |
| `SERVER_ERROR`           | server_error             |