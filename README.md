# RSS Aggregator

This application aggregates multiple RSS feeds from various websites and stores them in a centralized database. Subscribing to content is made easy and convenient, without the need to visit different websites or pages.

## Local Development

Make sure you're on Go version 1.20+.

Create a `.env` file in the root of the project with the following contents:

```bash
PORT="8000"
DB_URL=[YOUR_POSTGRES_DB_URL]
```

Perform DB migrations

```bash
cd sql/schema && goose postgres postgres://karokojnr:@localhost:5432/rssagg up && cd ../../ && sqlc generate
```

Run the server:

```bash
go build -o didactic-octo-guacamole && ./didactic-octo-guacamole
```


