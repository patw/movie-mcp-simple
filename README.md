# Movie Database MCP Server (Simplified)

A FastMCP server that provides access to a MongoDB movie database with natural language queries.

## Features

- Search movies by title, genre, actor, year, or rating
- Get top-rated movies by year or genre
- Count movies matching criteria
- Get detailed information about specific movies

## Prerequisites

- Python 3.7+
- MongoDB (local or cloud)
- `sample_mflix` database with `movies` collection

## Installation

1. Clone this repository:
```bash
git clone https://github.com/patw/movie-mcp-simple.git
cd movie-mcp-simple
```

2. Install dependencies:
```bash
pip install pymongo fastmcp python-dotenv
```

3. Create a `.env` file with your MongoDB connection string:
```bash
cp sample.env .env
```

Edit the `.env` file to add your actual MongoDB URI.

## Usage

Configure the MCP server in Claude desktop with the following config:

```
{
"mcpServers": {
"Movie Database": {
      "command": "uv",
      "args": [
        "run",
        "--with",
        "fastmcp, pymongo",
        "fastmcp",
        "run",
        "<path to>/movie-mcp-simple/movie-mcp.py"
      ]
    }
  }
}
```

Example queries you can ask:
- "Find movies with Tom Hanks"
- "How many Comedy movies are there?"
- "What are the top 5 movies from 1994?"
- "Show me details for The Shawshank Redemption"

## MCP Tools

The server provides these tools:

### `find_movies`
Search for movies with various filters:
```python
find_movies(title=None, genre=None, actor=None, year=None, min_rating=None, limit=10)
```

### `count_movies`
Count movies matching criteria:
```python
count_movies(genre=None, year=None, min_rating=None)
```

### `get_top_movies`
Get highest rated movies:
```python
get_top_movies(year=None, genre=None, limit=5)
```

### `get_movie_details`
Get full details for a specific movie:
```python
get_movie_details(title)
```

## License

MIT
