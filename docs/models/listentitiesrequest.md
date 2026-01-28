# ListEntitiesRequest


## Fields

| Field                                           | Type                                            | Required                                        | Description                                     |
| ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- |
| `search`                                        | *Optional[str]*                                 | :heavy_minus_sign:                              | Search by name or description                   |
| `index_id`                                      | *Optional[str]*                                 | :heavy_minus_sign:                              | Filter by index ID                              |
| `exact`                                         | *Optional[bool]*                                | :heavy_minus_sign:                              | Use exact name matching instead of fuzzy search |
| `limit`                                         | *Optional[int]*                                 | :heavy_minus_sign:                              | Maximum number of results                       |