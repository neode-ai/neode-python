# TripleBatchCreate


## Fields

| Field                                                  | Type                                                   | Required                                               | Description                                            |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| `triples`                                              | List[[models.TripleCreate](../models/triplecreate.md)] | :heavy_check_mark:                                     | N/A                                                    |
| `graph_id`                                             | *Optional[str]*                                        | :heavy_minus_sign:                                     | Default graph for all triples                          |
| `index_id`                                             | *str*                                                  | :heavy_check_mark:                                     | Index for entity disambiguation (required)             |
| `source`                                               | *Optional[str]*                                        | :heavy_minus_sign:                                     | Default source for all triples                         |