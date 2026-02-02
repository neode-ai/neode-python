# GenerateTriplesResponse

Response from generating triples with AI


## Fields

| Field                                      | Type                                       | Required                                   | Description                                |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `success`                                  | *Optional[bool]*                           | :heavy_minus_sign:                         | N/A                                        |
| `data`                                     | List[[models.Triple](../models/triple.md)] | :heavy_minus_sign:                         | N/A                                        |
| `count`                                    | *Optional[int]*                            | :heavy_minus_sign:                         | N/A                                        |
| `provider`                                 | *Optional[str]*                            | :heavy_minus_sign:                         | AI provider used (openai)                  |
| `credits_used`                             | *Optional[int]*                            | :heavy_minus_sign:                         | Credits deducted for generation            |
| `balance_remaining`                        | *Optional[int]*                            | :heavy_minus_sign:                         | Remaining credit balance                   |