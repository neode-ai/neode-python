<!-- Start SDK Example Usage [usage] -->
```python
# Synchronous Example
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.triples.query(limit=50)

    # Handle response
    print(res)
```

</br>

The same SDK client can also be used to make asynchronous requests by importing asyncio.

```python
# Asynchronous Example
import asyncio
from neode import Neode
import os

async def main():

    async with Neode(
        bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
    ) as n_client:

        res = await n_client.triples.query_async(limit=50)

        # Handle response
        print(res)

asyncio.run(main())
```
<!-- End SDK Example Usage [usage] -->