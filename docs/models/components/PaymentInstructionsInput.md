# PaymentInstructionsInput


## Supported Types

### Discriminator: `type`

| Value | Type |
| ----- | ---- |
| `"ach"` | [AchInstructionsInput](../../models/components/AchInstructionsInput.md) |
| `"domestic_wire"` | [DomesticWireInstructionsInput](../../models/components/DomesticWireInstructionsInput.md) |
| `"international_wire"` | [InternationalWireInstructionsInput](../../models/components/InternationalWireInstructionsInput.md) |

### [`AchInstructionsInput`](../../models/components/AchInstructionsInput.md)

Discriminator value: `"ach"`

```java
PaymentInstructionsInput value = AchInstructionsInput.builder()
    .type(AchInstructionsInputType.ACH)
    .beneficiaryName("Jane Doe")
    .accountNumber("123456789")
    .bankName("Bank of America")
    .branchCode("123456")
    .routingNumber("021000021")
    .build();
```

**Referred Types:** [AchInstructionsInputType](../../models/components/AchInstructionsInputType.md)

### [`DomesticWireInstructionsInput`](../../models/components/DomesticWireInstructionsInput.md)

Discriminator value: `"domestic_wire"`

```java
PaymentInstructionsInput value = DomesticWireInstructionsInput.builder()
    .type(DomesticWireInstructionsInputType.DOMESTIC_WIRE)
    .beneficiaryName("Jane Doe")
    .accountNumber("123456789")
    .bankName("Bank of America")
    .branchCode("123456")
    .intermediaryPartyName("Intermediary Bank")
    .intermediaryPartySwiftCode("INTBANKXXX")
    .originatorToBeneficiaryInstructionsLine1("For further credit to Jane Doe")
    .originatorToBeneficiaryInstructionsLine2("Invoice 12345")
    .originatorToBeneficiaryInstructionsLine3("Attn Accounts Payable")
    .routingNumber("021000021")
    .address(WireAddress.builder()
        .street1("123 Main St")
        .city("San Francisco")
        .countryCode("US")
        .street2("Suite 100")
        .state("CA")
        .postalCode("94105")
        .build())
    .build();
```

**Referred Types:** [DomesticWireInstructionsInputType](../../models/components/DomesticWireInstructionsInputType.md), [WireAddress](../../models/components/WireAddress.md)

### [`InternationalWireInstructionsInput`](../../models/components/InternationalWireInstructionsInput.md)

Discriminator value: `"international_wire"`

```java
PaymentInstructionsInput value = InternationalWireInstructionsInput.builder()
    .type(InternationalWireInstructionsInputType.INTERNATIONAL_WIRE)
    .beneficiaryName("Jane Doe")
    .accountNumber("123456789")
    .bankName("Bank of America")
    .branchCode("123456")
    .intermediaryPartyName("Intermediary Bank")
    .intermediaryPartySwiftCode("INTBANKXXX")
    .originatorToBeneficiaryInstructionsLine1("For further credit to Jane Doe")
    .originatorToBeneficiaryInstructionsLine2("Invoice 12345")
    .originatorToBeneficiaryInstructionsLine3("Attn Accounts Payable")
    .swiftCode("BOFAUS3N")
    .address(WireAddress.builder()
        .street1("123 Main St")
        .city("San Francisco")
        .countryCode("US")
        .street2("Suite 100")
        .state("CA")
        .postalCode("94105")
        .build())
    .build();
```

**Referred Types:** [InternationalWireInstructionsInputType](../../models/components/InternationalWireInstructionsInputType.md), [WireAddress](../../models/components/WireAddress.md)

## Consumption Patterns

### Java 11+ (Discriminator Switch)

```java
switch (value.type()) {
    case "ach":
        // Handle ach discriminator variant
        break;
    case "domestic_wire":
        // Handle domestic_wire discriminator variant
        break;
    case "international_wire":
        // Handle international_wire discriminator variant
        break;
    default:
        // Handle unknown discriminator variant
}
```

### Java 16+ (Instanceof Pattern Matching)

```java
if (value instanceof AchInstructionsInput achInstructionsInput) {
    // Handle AchInstructionsInput variant
} else if (value instanceof DomesticWireInstructionsInput domesticWireInstructionsInput) {
    // Handle DomesticWireInstructionsInput variant
} else if (value instanceof InternationalWireInstructionsInput internationalWireInstructionsInput) {
    // Handle InternationalWireInstructionsInput variant
} else {
    // Handle unknown discriminator variant
}
```

### Java 21+ (Type Pattern Switch)

```java
switch (value) {
    case AchInstructionsInput achInstructionsInput -> {
        // Handle AchInstructionsInput variant
    }
    case DomesticWireInstructionsInput domesticWireInstructionsInput -> {
        // Handle DomesticWireInstructionsInput variant
    }
    case InternationalWireInstructionsInput internationalWireInstructionsInput -> {
        // Handle InternationalWireInstructionsInput variant
    }
    default -> {
        // Handle unknown discriminator variant
    }
}
```
