# Blog Aggregator (aka gator)

## Requirements
* Go (v1.26 or later)
* Postgres (v15 or later)
* goose (v3.27.0)

## Tools Used
* sqlc (v1.30.0)
## Installation
### Step 1. Database Creation
Enter the `psql` shell:
* Mac: `psql postgres`
* Linux: `sudo -u postgres psql`

Create a new database. I called mine `gator`.
```
CREATE DATABASE gator;
```

### Step 2. Database Migration with Goose
In your console, navigate to the `sql/schema` directory. Run the following Goose command to create the required tables.
```
goose postgres <connection_string> up

# example:
# goose postgres "postgres://postgres:postgres@localhost:5432/gator" up
```

### Step 3. Command Line Installation
In your console, navigate to the project directory. Run the following command to install the application.
```
go install .
```

### Step 4. Register a User
In your console, run the following command:
```
blogaggregator register <name>
```

## Usage
| Command | Arguments | Description |
| --- | --- | --- |
| `register` | `<name>` | Register a new user. This user is set as the currently logged in user. |
| `login` | `<name>` | Switch the currently logged in user. |
| `reset` | | Resets the database by deleting all records, including users. <br>Note: remember to register a new user before running other commands. |
| `users` | | Prints the list of users to the console and notes the current user. |
| `agg` | `<time_between_requests>` | Reads all feeds and stores the posts. |
| `addfeed` | `<name> <url>` | Registers a new feed for the app to aggregate. Provide a name and the url for the feed as arguments. The current user will follow this feed. |
| `feeds` | | Lists all registered feeds. |
| `follow` | `<feed_url>` | Have the current user follow a previously registered feed given the url. |
| `following` | | List the registered feeds followed by the current user. |
| `unfollow` | `<feed_url>` | Have the current user unfollow a feed given the url. |
| `browse` | `<limit>` | Retrieves a list of recently aggregated posts from the feeds that the current user is following and prints them to the console. <br>Note: The `limit` argument is optional. Running without a limit will print two posts only. |
| Reads all feeds and stores the posts. |
| `addfeed` | `<name> <url>` | Registers a new feed for the app to aggregate. Provide a name and the url for the feed as arguments. The current user will follow this feed. |
| `feeds` | | Lists all registered feeds. |
| `follow` | `<feed_url>` | Have the current user follow a previously registered feed given the url. |
| `following` | | List the registered feeds followed by the current user. |
| `unfollow` | `<feed_url>` | Have the current user unfollow a feed given the url. |
| `browse` | `<limit>` | Retrieves a list of recently aggregated posts from the feeds that the current user is following and prints them to the console. <br>Note: The `limit` argument is optional. Running without a limit will print two posts only. |

