# Index

An index for organizing and disambiguating entities


## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `id`                                                                 | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `name`                                                               | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `description`                                                        | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `is_public`                                                          | *Optional[bool]*                                                     | :heavy_minus_sign:                                                   | N/A                                                                  |
| `preferred_predicates`                                               | List[*str*]                                                          | :heavy_minus_sign:                                                   | Preferred predicate types for this index                             |
| `rules`                                                              | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | Custom rules or instructions for triple generation in this index     |
| `item_count`                                                         | *Optional[int]*                                                      | :heavy_minus_sign:                                                   | Number of entities in this index                                     |
| `created_at`                                                         | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | N/A                                                                  |
| `updated_at`                                                         | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | N/A                                                                  |