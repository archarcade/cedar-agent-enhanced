# Cedar Policy Decision Point Agent

This Docker image contains a Cedar policy decision point (PDP) agent that provides authorization services for database systems.

## Image Details

- **Base**: Alpine Linux
- **Architecture**: Multi-platform (amd64, arm64)
- **Language**: Rust

## Features

- AWS Cedar policy evaluation engine
- REST API for authorization decisions
- Schema and entity management
- Policy management and validation
- High-performance concurrent request handling
- Health check endpoint

## Usage

```bash
docker pull ghcr.io/archarcade/cedar-agent:latest

docker run -d \
  -p 8180:8180 \
  -v ./schemas:/app/schemas:ro \
  ghcr.io/archarcade/cedar-agent:latest \
  -l info \
  -s /app/schemas/schema.json \
  -d /app/schemas/data.json \
  --policies /app/schemas/policies.json \
  --addr 0.0.0.0
```

## API Endpoints

- `GET /v1/health` - Health check
- `POST /v1/authorize` - Authorization decision
- `GET /v1/policies` - List policies
- `POST /v1/entities` - Manage entities

## Configuration

Command-line options:
- `-l, --log-level` - Log level (debug, info, warn, error)
- `-s, --schema` - Cedar schema file path
- `-d, --data` - Entity data file path
- `--policies` - Policies file path
- `--addr` - Bind address (default: 127.0.0.1)

## Related

- PostgreSQL with Cedar: `ghcr.io/archarcade/postgres-cedar`
- MySQL with Cedar: `ghcr.io/archarcade/mysql`
- Research: See accompanying research paper
