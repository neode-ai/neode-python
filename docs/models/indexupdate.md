# IndexUpdate

Fields to update on an index


## Fields

| Field                                                            | Type                                                             | Required                                                         | Description                                                      |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| `name`                                                           | *Optional[str]*                                                  | :heavy_minus_sign:                                               | N/A                                                              |
| `description`                                                    | *Optional[str]*                                                  | :heavy_minus_sign:                                               | N/A                                                              |
| `is_public`                                                      | *Optional[bool]*                                                 | :heavy_minus_sign:                                               | N/A                                                              |
| `preferred_predicates`                                           | List[*str*]                                                      | :heavy_minus_sign:                                               | Preferred predicate types for this index                         |
| `rules`                                                          | *Optional[str]*                                                  | :heavy_minus_sign:                                               | Custom rules or instructions for triple generation in this index |