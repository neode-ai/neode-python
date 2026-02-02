# SemanticSearchDataEntity

An entity representing a subject or object in the knowledge graph


## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `id`                                                                 | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `name`                                                               | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | Canonical name of the entity                                         |
| `description`                                                        | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `avatar_url`                                                         | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `index_id`                                                           | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `index_name`                                                         | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `created_at`                                                         | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | N/A                                                                  |
| `updated_at`                                                         | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | N/A                                                                  |
| `similarity`                                                         | *Optional[float]*                                                    | :heavy_minus_sign:                                                   | Similarity score (0-1)                                               |
| `triple_count`                                                       | *Optional[int]*                                                      | :heavy_minus_sign:                                                   | Number of related triples                                            |