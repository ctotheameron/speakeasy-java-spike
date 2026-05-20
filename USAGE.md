<!-- Start SDK Example Usage [usage] -->
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
<!-- End SDK Example Usage [usage] -->