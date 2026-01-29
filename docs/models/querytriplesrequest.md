# QueryTriplesRequest


## Fields

| Field                                                         | Type                                                          | Required                                                      | Description                                                   |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `search`                                                      | *Optional[str]*                                               | :heavy_minus_sign:                                            | Full-text search across subject, predicate, and object        |
| `subject`                                                     | *Optional[str]*                                               | :heavy_minus_sign:                                            | Filter by exact subject match                                 |
| `graph_id`                                                    | *Optional[str]*                                               | :heavy_minus_sign:                                            | Filter by graph ID                                            |
| `index_id`                                                    | *Optional[str]*                                               | :heavy_minus_sign:                                            | Filter by index ID                                            |
| `subject_entity_id`                                           | *Optional[str]*                                               | :heavy_minus_sign:                                            | Filter by subject entity ID                                   |
| `object_entity_id`                                            | *Optional[str]*                                               | :heavy_minus_sign:                                            | Filter by object entity ID                                    |
| `predicate`                                                   | *Optional[str]*                                               | :heavy_minus_sign:                                            | Filter by predicate (can be repeated for multiple predicates) |
| `offset`                                                      | *Optional[int]*                                               | :heavy_minus_sign:                                            | Number of results to skip for pagination                      |
| `limit`                                                       | *Optional[int]*                                               | :heavy_minus_sign:                                            | Maximum number of results                                     |