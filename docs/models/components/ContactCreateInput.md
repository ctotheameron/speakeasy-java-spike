# ContactCreateInput


## Fields

| Field                                 | Setter Type                           | Getter Type                           | Required                              | Description                           | Example                               |
| ------------------------------------- | ------------------------------------- | ------------------------------------- | ------------------------------------- | ------------------------------------- | ------------------------------------- |
| `name`                                | *String*                              | *String*                              | :heavy_check_mark:                    | Full legal name                       | Jane Doe                              |
| `email`                               | *String*                              | *String*                              | :heavy_check_mark:                    | Email address                         | jane.doe@example.com                  |
| `externalReferences`                  | @Nullable List\<*String*>             | Optional\<List\<*String*>>            | :heavy_minus_sign:                    | Your own identifiers for this contact | [<br/>"contact-123"<br/>]             |