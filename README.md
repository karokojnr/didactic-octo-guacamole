# RSS Aggregator

This application aggregates multiple RSS feeds from various websites and stores them in a centralized database. Subscribing to content is made easy and convenient, without the need to visit different websites or pages.

## Prerequisites
 - Go version 1.20+
 - PostgreSQL 14+
 - sqlc 1.24.0
 - goose 3.17.0

## Local Development

Create a `.env` file in the root of the project with the following contents:

```bash
PORT= "8000"
DB_URL= "[YOUR_POSTGRES_DB_URL]"
```

Perform DB migrations

```bash
cd sql/schema && goose postgres postgres://karokojnr:@localhost:5432/rssagg up && cd ../../ && sqlc generate
```

Run the server:

```bash
go build -o didactic-octo-guacamole && ./didactic-octo-guacamole
```

## API Endpoints
| Method | Endpoints | Action |
| --- | --- | --- |
| POST | /api/v1/users | To create a new users and assign API key |
| GET | /api/v1/users | To retrieves user details |
| POST | /api/v1/feeds | To create a new feed |
| GET | /api/v1/feeds | To retrieve all feeds |
| POST | /api/v1/feed-follows | To follow a feed |
| GET | /api/v1/feed-follows | To retrieve followed feeds |
| DELETE | /api/v1/feed-follows/:feedFollowID | To unfollow a feed |
| GET | /api/v1/posts | To retrieve posts from followed feeds |


## Authorization


Some requests require the use of API key.

To authenticate an API request, you should provide your API key in the `Authorization` header:

```bash
Authorization ApiKey [API_KEY]
``````

These request are:
    
    - GET    /api/v1/users
    - POST   /api/v1/feeds
    - POST   /api/v1/feed-follows
    - GET    /api/v1/feed-follows
    - DELETE /api/v1/feed-follows/:feedFollowID
    - GET    /api/v1/posts
