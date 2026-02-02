# SemanticSearchResponse

Response from semantic search


## Fields

| Field                                                                    | Type                                                                     | Required                                                                 | Description                                                              |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| `success`                                                                | *Optional[bool]*                                                         | :heavy_minus_sign:                                                       | N/A                                                                      |
| `data`                                                                   | [Optional[models.SemanticSearchData]](../models/semanticsearchdata.md)   | :heavy_minus_sign:                                                       | Search results data containing entities, triples, and graphs             |
| `count`                                                                  | [Optional[models.SemanticSearchCount]](../models/semanticsearchcount.md) | :heavy_minus_sign:                                                       | Count of search results by type                                          |