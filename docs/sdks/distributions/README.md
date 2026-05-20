# Distributions

## Overview

Manage distributions

### Available Operations

* [createDistributions](#createdistributions) - Create distributions
* [getDistribution](#getdistribution) - Retrieve a distribution

## createDistributions

Create one or more staged fund distributions in a single request. Each distribution has one or more payments; each payment references an existing entity by ID (`entity`) and an optional list of contacts to notify (`notifications[].contact`). Create entities and contacts first via `POST /entities` and `POST /contacts`. The batch is atomic — if any distribution fails validation, none are created.

### Example Usage

<!-- UsageSnippet language="java" operationID="createDistributions" method="post" path="/distributions" -->
```java
package hello.world;

import java.lang.Exception;
import java.time.OffsetDateTime;
import java.util.List;
import net.nova.api.NovaSDK;
import net.nova.api.models.components.DistributionInput;
import net.nova.api.models.errors.Error;
import net.nova.api.models.operations.CreateDistributionsResponse;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        NovaSDK sdk = NovaSDK.builder()
                .oAuth2(System.getenv().getOrDefault("O_AUTH2", ""))
            .build();

        CreateDistributionsResponse res = sdk.distributions().createDistributions()
                .xOrganizationId("org_Xk7d2pQR9m3nBwYz")
                .body(List.of(
                    DistributionInput.builder()
                        .name("April 20th Distribution from XYZ Sale")
                        .distributionDate(OffsetDateTime.parse("2024-04-20T00:00:00Z"))
                        .vehicle("<value>")
                        .payments(List.of())
                        .build()))
                .call();

        if (res.distributionList().isPresent()) {
            System.out.println(res.distributionList().get());
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                                   | Type                                                                                                                                                        | Required                                                                                                                                                    | Description                                                                                                                                                 | Example                                                                                                                                                     |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `xOrganizationId`                                                                                                                                           | *String*                                                                                                                                                    | :heavy_check_mark:                                                                                                                                          | ID of the organization the request acts on                                                                                                                  | org_Xk7d2pQR9m3nBwYz                                                                                                                                        |
| `idempotencyKey`                                                                                                                                            | @Nullable *String*                                                                                                                                          | :heavy_minus_sign:                                                                                                                                          | Unique key for idempotent requests. If you retry a request with the same key, the API returns the original response without performing the operation again. |                                                                                                                                                             |
| `body`                                                                                                                                                      | List\<[DistributionInput](../../models/components/DistributionInput.md)>                                                                                    | :heavy_check_mark:                                                                                                                                          | N/A                                                                                                                                                         |                                                                                                                                                             |

### Response

**[CreateDistributionsResponse](../../models/operations/CreateDistributionsResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 400, 401, 403, 404, 409    | application/json           |
| models/errors/Error        | 429                        | application/json           |
| models/errors/Error        | 500, 502                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getDistribution

Retrieve a distribution with aggregated payment status.

### Example Usage

<!-- UsageSnippet language="java" operationID="getDistribution" method="get" path="/distributions/{id}" -->
```java
package hello.world;

import java.lang.Exception;
import net.nova.api.NovaSDK;
import net.nova.api.models.errors.Error;
import net.nova.api.models.operations.GetDistributionResponse;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        NovaSDK sdk = NovaSDK.builder()
                .oAuth2(System.getenv().getOrDefault("O_AUTH2", ""))
            .build();

        GetDistributionResponse res = sdk.distributions().getDistribution()
                .id("<id>")
                .xOrganizationId("org_Xk7d2pQR9m3nBwYz")
                .call();

        if (res.distribution().isPresent()) {
            System.out.println(res.distribution().get());
        }
    }
}
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                | Example                                    |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `id`                                       | *String*                                   | :heavy_check_mark:                         | ID of the distribution                     |                                            |
| `xOrganizationId`                          | *String*                                   | :heavy_check_mark:                         | ID of the organization the request acts on | org_Xk7d2pQR9m3nBwYz                       |

### Response

**[GetDistributionResponse](../../models/operations/GetDistributionResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 403, 404              | application/json           |
| models/errors/Error        | 429                        | application/json           |
| models/errors/Error        | 500, 502                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |