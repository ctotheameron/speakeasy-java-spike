# speakeasy-java-spike

Generated Java SDK for the Nova API, produced by [Speakeasy](https://www.speakeasy.com/) from the OpenAPI spec in [`angellistventure/api-gateway`](https://github.com/angellistventure/api-gateway) (`api/openapi/nova/openapi.yaml`).

This repo is consumed as a git submodule at `api/openapi/nova/java-sdk` in api-gateway. It exists to evaluate Speakeasy as an alternative to our current Stainless-based SDK pipeline.

## How it works

1. A spec change lands on `main` in api-gateway.
2. api-gateway CI publishes the spec to the Speakeasy registry and dispatches `sdk_generation.yaml` here via `gh workflow run`.
3. `sdk_generation.yaml` runs `speakeasy run` to regenerate the Java SDK and commits the result directly to `main`.
4. A `repository_dispatch` fires back at api-gateway, which opens a PR bumping the submodule pointer.

## Local regen

```sh
speakeasy run
```

(requires `SPEAKEASY_API_KEY` env var; install the CLI via `brew install speakeasy-api/homebrew-tap/speakeasy`).
