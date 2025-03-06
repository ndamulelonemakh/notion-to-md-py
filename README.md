# notion-to-md (Python Version)

This is the **Python implementation** of nodejs version of [notion-to-md](https://github.com/souvikinator/notion-to-md),
a tool that converts Notion pages into Markdown files.

## Installation

Install the package via pip:

```bash
pip install notion-to-md-py
```

## Usage

### Sync Version

```python
from notion_client import Client
from notion_to_md import NotionToMarkdown


notion = Client(auth="your-auth-token")

n2m = NotionToMarkdown(notion)

# Export a page as a markdown blocks
md_blocks = n2m.page_to_markdown("page-id")

# Convert markdown blocks to string
md_str = n2m.to_markdown_string(md_blocks).get('parent')

# Write to a file
with open("output.md", "w") as f:
    f.write(md_str)
```

### Async Version

```python
import asyncio
from notion_client import AsyncClient
from notion_to_md import NotionToMarkdownAsync


notion = AsyncClient(auth="your-auth-token")

n2m = NotionToMarkdownAsync(notion)

# Export a page as a markdown blocks
md_blocks = asyncio.run(n2m.page_to_markdown("page-id"))

# Convert markdown blocks to string
md_str = n2m.to_markdown_string(md_blocks).get('parent')

# Write to a file
with open("output.md", "w") as f:
    f.write(md_str)
```

Replace `your-auth-token` and `page-id` with the appropriate values from your Notion account.

## Authentication with Notion API

1. Create an integration in your Notion account and get the `API key`.
2. Share your database with the integration to allow access.
3. Retrieve your `Database ID` and `Page ID` from the Notion app.

## Requirements

- Python 3.11 or later
- Notion API key

## Testing

You can run tests using either tox (for testing across multiple Python versions) or pytest directly.

### Running tests with tox

Tox allows you to test the package against multiple Python environments:

```bash
# Install tox
pip install tox

# Run tests on all supported Python versions
tox

# Run tests on a specific Python version
tox -e py311
```

### Running tests with pytest

For quicker test runs during development:

```bash
# Install test dependencies
pip install pytest

# Run all tests
pytest

# Run tests with coverage report
pytest --cov=notion_to_md
```

## Limitations

- The tool relies on the Notion API, and features are limited to what the API supports.
- Embedding or downloading files other than images is not supported.

## Contributing

Contributions are welcome! Feel free to open issues or submit pull requests to improve the functionality or fix bugs.

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Submit a pull request with a clear description of your changes.

## License

This project is licensed under the [MIT License](LICENSE).
