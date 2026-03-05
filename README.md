# docker-openclaw

Docker Compose configuration for running [OpenClaw](https://github.com/openclaw/openclaw).

## Requirements

- Docker
- Docker Compose v2

## Setup

```sh
cp .env.example .env
```

Edit `.env` and set `OPENCLAW_GATEWAY_TOKEN`:

```sh
# Generate a token
openssl rand -hex 32
```

## Usage

Start the gateway:

```sh
docker compose up -d
```

Connect via CLI:

```sh
docker compose run --rm cli
```

Stop:

```sh
docker compose down
```

## Services

| Service   | Description                        | Port         |
| --------- | ---------------------------------- | ------------ |
| `gateway` | OpenClaw gateway server            | 18789, 18790 |
| `cli`     | OpenClaw CLI (connects to gateway) | -            |

## Data

Persistent data is stored under `./data/`:

- `data/config/` — OpenClaw configuration and memory
- `data/workspace/` — Workspace files

## Environment Variables

See [`.env.example`](.env.example) for all available options.

| Variable                 | Required | Description                       |
| ------------------------ | -------- | --------------------------------- |
| `OPENCLAW_GATEWAY_TOKEN` | Yes      | Authentication token for gateway  |
| `OPENCLAW_GATEWAY_PORT`  | No       | Gateway API port (default: 18789) |
| `OPENCLAW_BRIDGE_PORT`   | No       | Bridge port (default: 18790)      |
| `OPENCLAW_GATEWAY_BIND`  | No       | Bind address (default: lan)       |
| `CLAUDE_AI_SESSION_KEY`  | No       | Claude AI session key             |
