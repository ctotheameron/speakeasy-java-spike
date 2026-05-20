# Authentication

## Overview

OAuth2 client_credentials token exchange

### Available Operations

* [createOAuthToken](#createoauthtoken) - Exchange client credentials for an access token

## createOAuthToken

RFC 6749 client_credentials grant. Authenticate with HTTP Basic auth (`Authorization: Basic <base64(client_id:client_secret)>`) or by passing `client_id` and `client_secret` in the request body. Returns a short-lived Bearer access token to use in the `Authorization` header on all other endpoints.

### Example Usage

<!-- UsageSnippet language="java" operationID="createOAuthToken" method="post" path="/oauth/token" -->
```java
package hello.world;

import java.lang.Exception;
import net.nova.api.NovaSDK;
import net.nova.api.models.components.GrantType;
import net.nova.api.models.components.OAuthTokenRequest;
import net.nova.api.models.errors.OAuthError;
import net.nova.api.models.operations.CreateOAuthTokenResponse;

public class Application {

    public static void main(String[] args) throws OAuthError, Exception {

        NovaSDK sdk = NovaSDK.builder()
            .build();

        OAuthTokenRequest req = OAuthTokenRequest.builder()
                .grantType(GrantType.CLIENT_CREDENTIALS)
                .scope("distributions:read entities:read")
                .build();

        CreateOAuthTokenResponse res = sdk.authentication().createOAuthToken()
                .request(req)
                .call();

        if (res.oAuthTokenResponse().isPresent()) {
            System.out.println(res.oAuthTokenResponse().get());
        }
    }
}
```

### Parameters

| Parameter                                                     | Type                                                          | Required                                                      | Description                                                   |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `request`                                                     | [OAuthTokenRequest](../../models/shared/OAuthTokenRequest.md) | :heavy_check_mark:                                            | The request object to use for the request.                    |

### Response

**[CreateOAuthTokenResponse](../../models/operations/CreateOAuthTokenResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/OAuthError   | 400, 401                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |