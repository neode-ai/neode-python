# SearchRequest

Request for semantic search across the knowledge graph


## Fields

| Field                                              | Type                                               | Required                                           | Description                                        |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| `query`                                            | *str*                                              | :heavy_check_mark:                                 | Natural language search query                      |
| `types`                                            | List[[models.SearchType](../models/searchtype.md)] | :heavy_minus_sign:                                 | Types of objects to search                         |
| `index_id`                                         | *Optional[str]*                                    | :heavy_minus_sign:                                 | Filter results to a specific index                 |
| `limit`                                            | *Optional[int]*                                    | :heavy_minus_sign:                                 | Maximum results per type                           |
| `threshold`                                        | *Optional[float]*                                  | :heavy_minus_sign:                                 | Minimum similarity score (0-1)                     |