# GenerateRequest

Request to generate triples using AI (OpenAI)


## Fields

| Field                                                         | Type                                                          | Required                                                      | Description                                                   |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `query`                                                       | *str*                                                         | :heavy_check_mark:                                            | Natural language description of what to extract triples about |
| `graph_id`                                                    | *Optional[str]*                                               | :heavy_minus_sign:                                            | Graph to store generated triples in                           |
| `index_id`                                                    | *str*                                                         | :heavy_check_mark:                                            | Index for entity disambiguation (required)                    |
| `web_search`                                                  | *Optional[bool]*                                              | :heavy_minus_sign:                                            | Enable web search for real-time information                   |
| `triple_count`                                                | *Optional[int]*                                               | :heavy_minus_sign:                                            | Target number of triples to generate (approximate)            |
| `predicates`                                                  | List[*str*]                                                   | :heavy_minus_sign:                                            | Restrict to specific predicate types                          |
| `subject_entity`                                              | *Optional[str]*                                               | :heavy_minus_sign:                                            | Constrain all generated triples to use this exact subject     |
| `rules`                                                       | *Optional[str]*                                               | :heavy_minus_sign:                                            | Custom rules or instructions for the AI generation            |
| `news_search`                                                 | *Optional[bool]*                                              | :heavy_minus_sign:                                            | Enable news-specific search for recent events                 |