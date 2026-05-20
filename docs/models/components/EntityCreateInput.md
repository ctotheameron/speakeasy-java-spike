# EntityCreateInput


## Fields

| Field                                               | Setter Type                                         | Getter Type                                         | Required                                            | Description                                         | Example                                             |
| --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- |
| `name`                                              | *String*                                            | *String*                                            | :heavy_check_mark:                                  | Legal name of the entity                            | Jane Doe, LLC                                       |
| `type`                                              | [EntityType](../../models/components/EntityType.md) | [EntityType](../../models/components/EntityType.md) | :heavy_check_mark:                                  | N/A                                                 | individual                                          |
| `externalReferences`                                | @Nullable List\<*String*>                           | Optional\<List\<*String*>>                          | :heavy_minus_sign:                                  | Your own identifiers for this entity                | [<br/>"entity-123"<br/>]                            |