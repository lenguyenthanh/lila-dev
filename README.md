# lila dev

My custom lichess development environment.

## Presquisites

- Docker
- JDK 21
- sbt

### Build some images

build `lila-ws` image:

```bash
git clone git@github.com:lenguyenthanh/lila-ws.git
cd lila-ws
sbt Docker/publishLocal
```

build `lila-fishnet` image:

```bash
git clone git@github.com:lichess-org/lila-fishnet.git
cd lila-fishnet
sbt Docker/publishLocal
```

## Usage

Start everything:

```bash
COMPOSE_PROFILES=all docker compose up -d
```

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


Stop them:

```bash
COMPOSE_PROFILES=all docker compose down
```

