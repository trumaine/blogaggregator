# Blog Aggregator (aka Gator)

A multi-player command line tool for aggregating RSS feeds and viewing the posts.

## Installation

Make sure you have the latest [Go toolchain](https://golang.org/dl/) installed as well as a local Postgres database. You can then install `blogaggregator` with:

```bash
go install ...
```

## Config

Create a `.gatorconfig.json` file in your home directory with the following structure:

```json
{
  "db_url": "postgres://username:@localhost:5432/database?sslmode=disable"
}
```

Replace the values with your database connection string.

## Usage

Create a new user:

```bash
blogaggregator register <name>
```

Add a feed:

```bash
gatoblogaggregatorr addfeed <url>
```

Start the aggregator:

```bash
blogaggregator agg 30s
```

View the posts:

```bash
blogaggregator browse [limit]
```

There are a few other commands you'll need as well:

- `blogaggregator login <name>` - Log in as a user that already exists
- `blogaggregator users` - List all users
- `blogaggregator feeds` - List all feeds
- `blogaggregator follow <url>` - Follow a feed that already exists in the database
- `blogaggregator unfollow <url>` - Unfollow a feed that already exists in the database
