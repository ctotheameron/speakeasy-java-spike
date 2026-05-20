# PaymentInstructions

## Overview

Manage payment instructions for entities

### Available Operations

* [createPaymentInstructions](#createpaymentinstructions) - Create payment instructions

## createPaymentInstructions

Create one or more payment instructions for one or more entities in a single request. Partial instructions are supported, and this endpoint does not do any input validation. The batch is atomic — if any fail to be created, none are created.

### Example Usage

<!-- UsageSnippet language="java" operationID="createPaymentInstructions" method="post" path="/payment_instructions" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import net.nova.api.NovaSDK;
import net.nova.api.models.components.EntityPaymentInstructionsInput;
import net.nova.api.models.components.InternationalWireInstructionsInput;
import net.nova.api.models.components.InternationalWireInstructionsInputType;
import net.nova.api.models.errors.Error;
import net.nova.api.models.operations.CreatePaymentInstructionsResponse;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        NovaSDK sdk = NovaSDK.builder()
                .oAuth2(System.getenv().getOrDefault("O_AUTH2", ""))
            .build();

        CreatePaymentInstructionsResponse res = sdk.paymentInstructions().createPaymentInstructions()
                .xOrganizationId("org_Xk7d2pQR9m3nBwYz")
                .body(List.of(
                    EntityPaymentInstructionsInput.builder()
                        .entity("ent_123")
                        .paymentInstructions(List.of(
                            InternationalWireInstructionsInput.builder()
                                .type(InternationalWireInstructionsInputType.INTERNATIONAL_WIRE)
                                .build()))
                        .build()))
                .call();

        if (res.entityPaymentInstructionsList().isPresent()) {
            System.out.println(res.entityPaymentInstructionsList().get());
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                                   | Type                                                                                                                                                        | Required                                                                                                                                                    | Description                                                                                                                                                 | Example                                                                                                                                                     |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `xOrganizationId`                                                                                                                                           | *String*                                                                                                                                                    | :heavy_check_mark:                                                                                                                                          | ID of the organization the request acts on                                                                                                                  | org_Xk7d2pQR9m3nBwYz                                                                                                                                        |
| `idempotencyKey`                                                                                                                                            | @Nullable *String*                                                                                                                                          | :heavy_minus_sign:                                                                                                                                          | Unique key for idempotent requests. If you retry a request with the same key, the API returns the original response without performing the operation again. |                                                                                                                                                             |
| `body`                                                                                                                                                      | List\<[EntityPaymentInstructionsInput](../../models/components/EntityPaymentInstructionsInput.md)>                                                          | :heavy_check_mark:                                                                                                                                          | N/A                                                                                                                                                         |                                                                                                                                                             |

### Response

**[CreatePaymentInstructionsResponse](../../models/operations/CreatePaymentInstructionsResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 400, 401, 403              | application/json           |
| models/errors/Error        | 429                        | application/json           |
| models/errors/Error        | 500, 502                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |