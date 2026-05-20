# EntityType

## Example Usage

```java
import net.nova.api.models.components.EntityType;

EntityType value = EntityType.INDIVIDUAL;

// Open enum: use .of() to create instances from custom string values
EntityType custom = EntityType.of("custom_value");
```


## Values

| Name                            | Value                           |
| ------------------------------- | ------------------------------- |
| `INDIVIDUAL`                    | individual                      |
| `INDIVIDUAL_RETIREMENT_PLAN`    | individual_retirement_plan      |
| `CORPORATION`                   | corporation                     |
| `LLC`                           | llc                             |
| `PARTNERSHIP`                   | partnership                     |
| `TRUST`                         | trust                           |
| `JOINT_TENANTS_ROS`             | joint_tenants_ros               |
| `TENANTS_IN_COMMON`             | tenants_in_common               |
| `COMMUNITY_PROPERTY`            | community_property              |
| `REGISTERED_INVESTMENT_COMPANY` | registered_investment_company   |
| `FOUNDATION`                    | foundation                      |
| `CHARITABLE_REMAINDER_TRUST`    | charitable_remainder_trust      |
| `ENDOWMENT`                     | endowment                       |
| `EMPLOYEE_BENEFIT_PLAN`         | employee_benefit_plan           |
| `KEOGH_PLAN`                    | keogh_plan                      |
| `OTHER_ENTITY`                  | other_entity                    |