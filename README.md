# lila dev

My custom lichess development environment.

## Usage

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

## Optional

Enable fishnet play:

```bash
docker compose up -d fishnet-play
docker compose up -d lila-fishnet
```


Stop them:

```bash
docker compose down fishnet-play
docker compose down lila-fishnet
```

