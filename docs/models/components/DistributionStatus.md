# DistributionStatus

## Example Usage

```java
import net.nova.api.models.components.DistributionStatus;

DistributionStatus value = DistributionStatus.DRAFT;

// Open enum: use .of() to create instances from custom string values
DistributionStatus custom = DistributionStatus.of("custom_value");
```


## Values

| Name        | Value       |
| ----------- | ----------- |
| `DRAFT`     | draft       |
| `PUBLISHED` | published   |
| `APPROVED`  | approved    |
| `EXECUTED`  | executed    |
| `CANCELLED` | cancelled   |