# Contacts

## Overview

Manage contacts

### Available Operations

* [createContacts](#createcontacts) - Create contacts
* [getContact](#getcontact) - Retrieve a contact

## createContacts

Create one or more contacts associated with the organization in a single request. The batch is atomic — if any contact fails validation, none are created.

### Example Usage

<!-- UsageSnippet language="java" operationID="createContacts" method="post" path="/contacts" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import net.nova.api.NovaSDK;
import net.nova.api.models.components.ContactCreateInput;
import net.nova.api.models.errors.Error;
import net.nova.api.models.operations.CreateContactsResponse;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        NovaSDK sdk = NovaSDK.builder()
                .oAuth2(System.getenv().getOrDefault("O_AUTH2", ""))
            .build();

        CreateContactsResponse res = sdk.contacts().createContacts()
                .xOrganizationId("org_Xk7d2pQR9m3nBwYz")
                .body(List.of(
                    ContactCreateInput.builder()
                        .name("Jane Doe")
                        .email("jane.doe@example.com")
                        .externalReferences(List.of(
                            "contact-123"))
                        .build()))
                .call();

        if (res.contactList().isPresent()) {
            System.out.println(res.contactList().get());
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                                   | Type                                                                                                                                                        | Required                                                                                                                                                    | Description                                                                                                                                                 | Example                                                                                                                                                     |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `xOrganizationId`                                                                                                                                           | *String*                                                                                                                                                    | :heavy_check_mark:                                                                                                                                          | ID of the organization the request acts on                                                                                                                  | org_Xk7d2pQR9m3nBwYz                                                                                                                                        |
| `idempotencyKey`                                                                                                                                            | @Nullable *String*                                                                                                                                          | :heavy_minus_sign:                                                                                                                                          | Unique key for idempotent requests. If you retry a request with the same key, the API returns the original response without performing the operation again. |                                                                                                                                                             |
| `body`                                                                                                                                                      | List\<[ContactCreateInput](../../models/components/ContactCreateInput.md)>                                                                                  | :heavy_check_mark:                                                                                                                                          | N/A                                                                                                                                                         |                                                                                                                                                             |

### Response

**[CreateContactsResponse](../../models/operations/CreateContactsResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 400, 401, 403, 409         | application/json           |
| models/errors/Error        | 429                        | application/json           |
| models/errors/Error        | 500, 502                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getContact

Retrieve a single contact by ID.

### Example Usage

<!-- UsageSnippet language="java" operationID="getContact" method="get" path="/contacts/{id}" -->
```java
package hello.world;

import java.lang.Exception;
import net.nova.api.NovaSDK;
import net.nova.api.models.errors.Error;
import net.nova.api.models.operations.GetContactResponse;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        NovaSDK sdk = NovaSDK.builder()
                .oAuth2(System.getenv().getOrDefault("O_AUTH2", ""))
            .build();

        GetContactResponse res = sdk.contacts().getContact()
                .id("cnt_123")
                .xOrganizationId("org_Xk7d2pQR9m3nBwYz")
                .call();

        if (res.contact().isPresent()) {
            System.out.println(res.contact().get());
        }
    }
}
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                | Example                                    |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `id`                                       | *String*                                   | :heavy_check_mark:                         | ID of the contact                          | cnt_123                                    |
| `xOrganizationId`                          | *String*                                   | :heavy_check_mark:                         | ID of the organization the request acts on | org_Xk7d2pQR9m3nBwYz                       |

### Response

**[GetContactResponse](../../models/operations/GetContactResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 403, 404              | application/json           |
| models/errors/Error        | 429                        | application/json           |
| models/errors/Error        | 500, 502                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |