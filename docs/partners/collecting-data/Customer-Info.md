---
tags: [marketplace]
---

## Available fields for `customerInfo`

| Field                         | Type              | Information                                                                                     |
| ----------------------------- | ----------------- | ----------------------------------------------------------------------------------------------- |
| email                         | String            | Max Length 255                                                                                  |
| title                         | String            | Max Length 10                                                                                   |
| first_name                    | String            | Max Length 255                                                                                  |
| surname                       | String            | Max Length 255                                                                                  |
| dob                           | Datetime ISO 8601 |
| phone_number                  | String            | Max Length 15                                                                                   |
| mobile_number                 | String            | Max Length 15                                                                                   |
| preferred_name                | String            | Max Length 255                                                                                  |
| passport_number               | String            | Max Length 50                                                                                   |
| national_insurance_number     | String            | Max Length 15                                                                                   |
| building_number               | String            | Max Length 50                                                                                   |
| address_1                     | String            | Max Length 50                                                                                   |
| address_2                     | String            | Max Length 50                                                                                   |
| address_3                     | String            | Max Length 50                                                                                   |
| town_city                     | String            | Max Length 50                                                                                   |
| county                        | String            | Max Length 50                                                                                   |
| postcode                      | String            | Max Length 8                                                                                    |
| country_of_residence          | String            | Max Length 50                                                                                   |
| nationality                   | String            | Max Length 50                                                                                   |
| gender                        | String            | Max Length 15                                                                                   |
| relationship_status           | String            | Max Length 50                                                                                   |
| number_of_children            | Integer           |
| partner_first_name            | String            | Max Length 255                                                                                  |
| partner_surname               | String            | Max Length 255                                                                                  |
| partner_dob                   | Datetime ISO 8601 |
| partner_sex                   | String            | Max Length 15                                                                                   |
| relationship_to_partner       | String            | Max Length 50                                                                                   |
| smoker                        | String            | "yes" / "no"                                                                                    |
| number_of_cigarettes_per_week | Integer           |
| drinker                       | String            | "yes" / "no"                                                                                    |
| number_of_units_per_week      | Integer           |
| meta                          | JSON              | Snake Case key. For any custom data not defined in the field column eg. `{ "custom_data": 10 }` |

> In the snippet, customerInfo is required but all fields are optional. We do suggest however that you provide as much information as you can to allow users to join services without having to ask for missing fields whenever a provider requires them.
