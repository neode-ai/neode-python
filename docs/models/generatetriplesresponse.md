# GenerateTriplesResponse

Response from generating triples with AI


## Fields

| Field                                                          | Type                                                           | Required                                                       | Description                                                    |
| -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- |
| `success`                                                      | *Optional[bool]*                                               | :heavy_minus_sign:                                             | N/A                                                            |
| `data`                                                         | List[[models.Triple](../models/triple.md)]                     | :heavy_minus_sign:                                             | N/A                                                            |
| `count`                                                        | *Optional[int]*                                                | :heavy_minus_sign:                                             | N/A                                                            |
| `graph_id`                                                     | *Optional[str]*                                                | :heavy_minus_sign:                                             | Graph ID the triples were stored in (auto-created or provided) |
| `provider`                                                     | *Optional[str]*                                                | :heavy_minus_sign:                                             | AI provider used (openai)                                      |
| `credits_used`                                                 | *Optional[int]*                                                | :heavy_minus_sign:                                             | Credits deducted for generation                                |
| `balance_remaining`                                            | *Optional[int]*                                                | :heavy_minus_sign:                                             | Remaining credit balance                                       |
| `auto_topup_triggered`                                         | *Optional[bool]*                                               | :heavy_minus_sign:                                             | Whether auto top-up was triggered after this generation        |