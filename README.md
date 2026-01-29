# Neode Python SDK

The official Python SDK for the [Neode](https://neode.ai) knowledge graph API. Build intelligent applications with a developer-friendly, type-safe interface for storing, querying, and generating knowledge triples.

[![PyPI](https://img.shields.io/pypi/v/neode.svg)](https://pypi.org/project/neode/)
[![Python Version](https://img.shields.io/pypi/pyversions/neode.svg)](https://pypi.org/project/neode/)
[![License: Apache-2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Built by Speakeasy](https://img.shields.io/badge/Built_by-Speakeasy-black)](https://www.speakeasy.com/?utm_source=neode&utm_campaign=python)


<!-- Start Summary [summary] -->
## Summary

Neode API: A knowledge graph API for storing, querying, and generating triples. Use Neode as a triples store for your LLM applications - store facts, query knowledge, and generate new triples from any context.
<!-- End Summary [summary] -->

## Features

- **Knowledge Graphs** - Store and query RDF-style triples (subject, predicate, object)
- **Semantic Search** - Find relevant knowledge using natural language queries
- **AI-Powered Generation** - Generate new triples from any text using LLMs
- **Full Async Support** - Native async/await for high-performance applications
- **Automatic Pagination** - Seamlessly iterate through large result sets
- **Built-in Retries** - Configurable retry logic with exponential backoff
- **Type Safety** - Full Pydantic models for request/response validation

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [neode](#neode)
  * [SDK Installation](#sdk-installation)
  * [IDE Support](#ide-support)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Pagination](#pagination)
  * [Retries](#retries)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
  * [Custom HTTP Client](#custom-http-client)
  * [Resource Management](#resource-management)
  * [Debugging](#debugging)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

> [!NOTE]
> **Python version upgrade policy**
>
> Once a Python version reaches its [official end of life date](https://devguide.python.org/versions/), a 3-month grace period is provided for users to upgrade. Following this grace period, the minimum python version supported in the SDK will be updated.

The SDK can be installed with *uv*, *pip*, or *poetry* package managers.

### uv

*uv* is a fast Python package installer and resolver, designed as a drop-in replacement for pip and pip-tools. It's recommended for its speed and modern Python tooling capabilities.

```bash
uv add neode
```

### PIP

*PIP* is the default package installer for Python, enabling easy installation and management of packages from PyPI via the command line.

```bash
pip install neode
```

### Poetry

*Poetry* is a modern tool that simplifies dependency management and package publishing by using a single `pyproject.toml` file to handle project metadata and dependencies.

```bash
poetry add neode
```

### Shell and script usage with `uv`

You can use this SDK in a Python shell with [uv](https://docs.astral.sh/uv/) and the `uvx` command that comes with it like so:

```shell
uvx --from neode python
```

It's also possible to write a standalone Python script without needing to set up a whole project like so:

```python
#!/usr/bin/env -S uv run --script
# /// script
# requires-python = ">=3.9"
# dependencies = [
#     "neode",
# ]
# ///

from neode import Neode

sdk = Neode(
  # SDK arguments
)

# Rest of script here...
```

Once that is saved to a file, you can run it with `uv run script.py` where
`script.py` can be replaced with the actual file name.
<!-- End SDK Installation [installation] -->

<!-- Start IDE Support [idesupport] -->
## IDE Support

### PyCharm

Generally, the SDK will work well with most IDEs out of the box. However, when using PyCharm, you can enjoy much better integration with Pydantic by installing an additional plugin.

- [PyCharm Pydantic Plugin](https://docs.pydantic.dev/latest/integrations/pycharm/)
<!-- End IDE Support [idesupport] -->

## Quick Start

Get up and running in minutes:

```python
import os
from neode import Neode

# Initialize the client
client = Neode(bearer_auth=os.getenv("NEODE_BEARER_AUTH"))

# Create a triple (fact)
client.triples.create(triples=[{
    "subject": "Python",
    "predicate": "is_a",
    "object": "programming_language"
}])

# Query your knowledge graph
results = client.triples.query(limit=10)
for triple in results.data:
    print(f"{triple.subject} -> {triple.predicate} -> {triple.object}")

# Generate new triples from text using AI
generated = client.generation.generate_triples(
    context="Albert Einstein developed the theory of relativity in 1905."
)
```

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```python
# Synchronous Example
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.triples.query(offset=0, limit=50)

    while res is not None:
        # Handle items

        res = res.next()
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

        res = await n_client.triples.query_async(offset=0, limit=50)

        while res is not None:
            # Handle items

            res = res.next()

asyncio.run(main())
```
<!-- End SDK Example Usage [usage] -->

## Getting Your API Key

To use the Neode SDK, you'll need an API key:

1. Sign up or log in at [neode.ai](https://neode.ai)
2. Navigate to **Settings** > **API Keys**
3. Click **Create API Key** and copy your new key
4. Set the key as an environment variable:

```bash
export NEODE_BEARER_AUTH="your-api-key-here"
```

The SDK automatically reads from the `NEODE_BEARER_AUTH` environment variable, or you can pass it directly when initializing the client.

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name          | Type | Scheme      | Environment Variable |
| ------------- | ---- | ----------- | -------------------- |
| `bearer_auth` | http | HTTP Bearer | `NEODE_BEARER_AUTH`  |

To authenticate with the API the `bearer_auth` parameter must be set when initializing the SDK client instance. For example:
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.triples.query(offset=0, limit=50)

    while res is not None:
        # Handle items

        res = res.next()

```
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [Entities](docs/sdks/entities/README.md)

* [list](docs/sdks/entities/README.md#list) - List entities
* [create](docs/sdks/entities/README.md#create) - Create an entity
* [get](docs/sdks/entities/README.md#get) - Get an entity
* [update](docs/sdks/entities/README.md#update) - Update an entity
* [delete](docs/sdks/entities/README.md#delete) - Delete an entity

### [Generation](docs/sdks/generation/README.md)

* [generate_triples](docs/sdks/generation/README.md#generate_triples) - Generate triples

### [Graphs](docs/sdks/graphs/README.md)

* [list_all](docs/sdks/graphs/README.md#list_all) - List graphs
* [create](docs/sdks/graphs/README.md#create) - Create a graph
* [get](docs/sdks/graphs/README.md#get) - Get a graph
* [delete](docs/sdks/graphs/README.md#delete) - Delete a graph

### [Indexes](docs/sdks/indexes/README.md)

* [list](docs/sdks/indexes/README.md#list) - List indexes
* [create](docs/sdks/indexes/README.md#create) - Create an index

### [Search](docs/sdks/search/README.md)

* [semantic_get](docs/sdks/search/README.md#semantic_get) - Semantic search (GET)
* [semantic](docs/sdks/search/README.md#semantic) - Semantic search (POST)

### [Triples](docs/sdks/triples/README.md)

* [query](docs/sdks/triples/README.md#query) - Query triples
* [create](docs/sdks/triples/README.md#create) - Create triples
* [update](docs/sdks/triples/README.md#update) - Update a triple
* [delete](docs/sdks/triples/README.md#delete) - Delete triples

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Pagination [pagination] -->
## Pagination

Some of the endpoints in this SDK support pagination. To use pagination, you make your SDK calls as usual, but the
returned response object will have a `Next` method that can be called to pull down the next group of results. If the
return value of `Next` is `None`, then there are no more pages to be fetched.

Here's an example of one such pagination call:
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.triples.query(offset=0, limit=50)

    while res is not None:
        # Handle items

        res = res.next()

```
<!-- End Pagination [pagination] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries. If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API. However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a `RetryConfig` object to the call:
```python
from neode import Neode
from neode.utils import BackoffStrategy, RetryConfig
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.triples.query(offset=0, limit=50,
        RetryConfig("backoff", BackoffStrategy(1, 50, 1.1, 100), False))

    while res is not None:
        # Handle items

        res = res.next()

```

If you'd like to override the default retry strategy for all operations that support retries, you can use the `retry_config` optional parameter when initializing the SDK:
```python
from neode import Neode
from neode.utils import BackoffStrategy, RetryConfig
import os


with Neode(
    retry_config=RetryConfig("backoff", BackoffStrategy(1, 50, 1.1, 100), False),
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.triples.query(offset=0, limit=50)

    while res is not None:
        # Handle items

        res = res.next()

```
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

[`NeodeError`](./src/neode/errors/neodeerror.py) is the base class for all HTTP error responses. It has the following properties:

| Property           | Type             | Description                                                                             |
| ------------------ | ---------------- | --------------------------------------------------------------------------------------- |
| `err.message`      | `str`            | Error message                                                                           |
| `err.status_code`  | `int`            | HTTP response status code eg `404`                                                      |
| `err.headers`      | `httpx.Headers`  | HTTP response headers                                                                   |
| `err.body`         | `str`            | HTTP body. Can be empty string if no body is returned.                                  |
| `err.raw_response` | `httpx.Response` | Raw HTTP response                                                                       |
| `err.data`         |                  | Optional. Some errors may contain structured data. [See Error Classes](#error-classes). |

### Example
```python
from neode import Neode, errors
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:
    res = None
    try:

        res = n_client.triples.query(offset=0, limit=50)

        while res is not None:
            # Handle items

            res = res.next()


    except errors.NeodeError as e:
        # The base class for HTTP error responses
        print(e.message)
        print(e.status_code)
        print(e.body)
        print(e.headers)
        print(e.raw_response)

        # Depending on the method different errors may be thrown
        if isinstance(e, errors.Error):
            print(e.data.success)  # Optional[bool]
            print(e.data.error)  # Optional[str]
            print(e.data.details)  # Optional[str]
```

### Error Classes
**Primary errors:**
* [`NeodeError`](./src/neode/errors/neodeerror.py): The base class for HTTP error responses.
  * [`Error`](./src/neode/errors/error.py): Bad request.

<details><summary>Less common errors (6)</summary>

<br />

**Network errors:**
* [`httpx.RequestError`](https://www.python-httpx.org/exceptions/#httpx.RequestError): Base class for request errors.
    * [`httpx.ConnectError`](https://www.python-httpx.org/exceptions/#httpx.ConnectError): HTTP client was unable to make a request to a server.
    * [`httpx.TimeoutException`](https://www.python-httpx.org/exceptions/#httpx.TimeoutException): HTTP request timed out.


**Inherit from [`NeodeError`](./src/neode/errors/neodeerror.py)**:
* [`PaymentRequiredError`](./src/neode/errors/paymentrequirederror.py): Insufficient credits. Status code `402`. Applicable to 1 of 18 methods.*
* [`ResponseValidationError`](./src/neode/errors/responsevalidationerror.py): Type mismatch between the response data and the expected Pydantic model. Provides access to the Pydantic validation error via the `cause` attribute.

</details>

\* Check [the method documentation](#available-resources-and-operations) to see if the error is applicable.
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Select Server by Index

You can override the default server globally by passing a server index to the `server_idx: int` optional parameter when initializing the SDK client instance. The selected server will then be used as the default on the operations that use it. This table lists the indexes associated with the available servers:

| #   | Server                  | Description       |
| --- | ----------------------- | ----------------- |
| 0   | `https://neode.ai`      | Production server |
| 1   | `http://localhost:5173` | Local development |

#### Example

```python
from neode import Neode
import os


with Neode(
    server_idx=0,
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.triples.query(offset=0, limit=50)

    while res is not None:
        # Handle items

        res = res.next()

```

### Override Server URL Per-Client

The default server can also be overridden globally by passing a URL to the `server_url: str` optional parameter when initializing the SDK client instance. For example:
```python
from neode import Neode
import os


with Neode(
    server_url="http://localhost:5173",
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.triples.query(offset=0, limit=50)

    while res is not None:
        # Handle items

        res = res.next()

```
<!-- End Server Selection [server] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The Python SDK makes API calls using the [httpx](https://www.python-httpx.org/) HTTP library.  In order to provide a convenient way to configure timeouts, cookies, proxies, custom headers, and other low-level configuration, you can initialize the SDK client with your own HTTP client instance.
Depending on whether you are using the sync or async version of the SDK, you can pass an instance of `HttpClient` or `AsyncHttpClient` respectively, which are Protocol's ensuring that the client has the necessary methods to make API calls.
This allows you to wrap the client with your own custom logic, such as adding custom headers, logging, or error handling, or you can just pass an instance of `httpx.Client` or `httpx.AsyncClient` directly.

For example, you could specify a header for every request that this sdk makes as follows:
```python
from neode import Neode
import httpx

http_client = httpx.Client(headers={"x-custom-header": "someValue"})
s = Neode(client=http_client)
```

or you could wrap the client with your own custom logic:
```python
from neode import Neode
from neode.httpclient import AsyncHttpClient
import httpx

class CustomClient(AsyncHttpClient):
    client: AsyncHttpClient

    def __init__(self, client: AsyncHttpClient):
        self.client = client

    async def send(
        self,
        request: httpx.Request,
        *,
        stream: bool = False,
        auth: Union[
            httpx._types.AuthTypes, httpx._client.UseClientDefault, None
        ] = httpx.USE_CLIENT_DEFAULT,
        follow_redirects: Union[
            bool, httpx._client.UseClientDefault
        ] = httpx.USE_CLIENT_DEFAULT,
    ) -> httpx.Response:
        request.headers["Client-Level-Header"] = "added by client"

        return await self.client.send(
            request, stream=stream, auth=auth, follow_redirects=follow_redirects
        )

    def build_request(
        self,
        method: str,
        url: httpx._types.URLTypes,
        *,
        content: Optional[httpx._types.RequestContent] = None,
        data: Optional[httpx._types.RequestData] = None,
        files: Optional[httpx._types.RequestFiles] = None,
        json: Optional[Any] = None,
        params: Optional[httpx._types.QueryParamTypes] = None,
        headers: Optional[httpx._types.HeaderTypes] = None,
        cookies: Optional[httpx._types.CookieTypes] = None,
        timeout: Union[
            httpx._types.TimeoutTypes, httpx._client.UseClientDefault
        ] = httpx.USE_CLIENT_DEFAULT,
        extensions: Optional[httpx._types.RequestExtensions] = None,
    ) -> httpx.Request:
        return self.client.build_request(
            method,
            url,
            content=content,
            data=data,
            files=files,
            json=json,
            params=params,
            headers=headers,
            cookies=cookies,
            timeout=timeout,
            extensions=extensions,
        )

s = Neode(async_client=CustomClient(httpx.AsyncClient()))
```
<!-- End Custom HTTP Client [http-client] -->

<!-- Start Resource Management [resource-management] -->
## Resource Management

The `Neode` class implements the context manager protocol and registers a finalizer function to close the underlying sync and async HTTPX clients it uses under the hood. This will close HTTP connections, release memory and free up other resources held by the SDK. In short-lived Python programs and notebooks that make a few SDK method calls, resource management may not be a concern. However, in longer-lived programs, it is beneficial to create a single SDK instance via a [context manager][context-manager] and reuse it across the application.

[context-manager]: https://docs.python.org/3/reference/datamodel.html#context-managers

```python
from neode import Neode
import os
def main():

    with Neode(
        bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
    ) as n_client:
        # Rest of application here...


# Or when using async:
async def amain():

    async with Neode(
        bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
    ) as n_client:
        # Rest of application here...
```
<!-- End Resource Management [resource-management] -->

<!-- Start Debugging [debug] -->
## Debugging

You can setup your SDK to emit debug logs for SDK requests and responses.

You can pass your own logger class directly into your SDK.
```python
from neode import Neode
import logging

logging.basicConfig(level=logging.DEBUG)
s = Neode(debug_logger=logging.getLogger("neode"))
```

You can also enable a default debug logger by setting an environment variable `NEODE_DEBUG` to true.
<!-- End Debugging [debug] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

## Support

- **Documentation**: [neode.ai/docs](https://neode.ai/docs)
- **Issues**: [GitHub Issues](https://github.com/neode-ai/neode-python/issues)
- **Email**: support@neode.ai

# Development

## Maturity

This SDK is in beta. While we strive for stability, there may be breaking changes between minor versions. We recommend pinning to a specific version in production:

```bash
# Lock to a specific version
uv add neode==0.2.1
```

## Contributions

This SDK is generated programmatically using [Speakeasy](https://www.speakeasy.com/?utm_source=neode&utm_campaign=python). While we welcome feedback and suggestions:

- **Bug reports**: Open an issue describing the problem and steps to reproduce
- **Feature requests**: Open an issue with your use case and proposed solution
- **API improvements**: Changes to the underlying API should be directed to the main Neode repository

Note: Direct code contributions to generated files will be overwritten on the next generation cycle.
