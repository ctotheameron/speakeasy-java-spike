# DistributionPaymentStatus

## Example Usage

```java
import net.nova.api.models.components.DistributionPaymentStatus;

DistributionPaymentStatus value = DistributionPaymentStatus.STAGED;

// Open enum: use .of() to create instances from custom string values
DistributionPaymentStatus custom = DistributionPaymentStatus.of("custom_value");
```


## Values

| Name                  | Value                 |
| --------------------- | --------------------- |
| `STAGED`              | staged                |
| `RECIPIENT_CONFIRMED` | recipient_confirmed   |
| `VERIFIED`            | verified              |
| `DISBURSED`           | disbursed             |
| `FAILED`              | failed                |