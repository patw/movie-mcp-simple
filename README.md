# Movie Database MCP Server

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
git clone https://github.com/yourusername/movie-mcp-server.git
cd movie-mcp-server
```

2. Install dependencies:
```bash
pip install pymongo fastmcp
```

3. Import the sample data (if needed):
```bash
mongorestore --uri mongodb://localhost:27017 --archive=sample_mflix.gz --gzip
```

## Usage

Run the server:
```bash
python movie-mcp.py mongodb://your_mongodb_uri
```

Example queries you can ask:
- "Find movies with Tom Hanks"
- "How many Comedy movies are there?"
- "What are the top 5 movies from 1994?"
- "Show me details for The Shawshank Redemption"

## API Endpoints

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
