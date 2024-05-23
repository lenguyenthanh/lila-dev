# lila dev

My custom lichess development environment.

This just contains a docker-compose file that has several [profiles](https://docs.docker.com/compose/profiles), so you can start/stop services as needed. This expect you to have the lila codebase locally and able to run it using sbt.

This is oriented towards [lila's](https://github.com/lichess-org/lila) development, but can also to use when working on specific services like `lila-ws` or `lila-fishnet`, by stopping the coressponding services and running the ones you working on.

It's highly opinionated and tailored to my needs, but you can use it as a starting point for your own development environment.



## Presquisites

- Docker
- JDK 21
- sbt

## Usage

Start everything:

```bash
COMPOSE_PROFILES=all docker compose up -d
```

Then go to lila directory and start the server:

```bash
sbt run
```

Now you should be able to access lila at `http://localhost:9663` and play with fishnet.

## Other usages

Or you can start only the services you need:

Start infra services (redis, postgres, etc) with:

```bash
COMPOSE_PROFILES=infra docker compose up -d
``````

Start lila-ws (need to build it's docker image first) with:

```bash
docker compose up -d lila-ws
```

You should be able to start lila and play around with it at this point.

If you're working on lila-ws, then stop it

```bash
docker compose down lila-ws
```

Enable fishnet play:

```bash
docker compose up -d fishnet-play
docker compose up -d lila-fishnet
```

Stop them all:

```bash
COMPOSE_PROFILES=all docker compose down
```

## Inspiration

- [lila-docker](https://github.com/lichess-org/lila-docker)
