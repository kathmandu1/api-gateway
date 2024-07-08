# Gateway

This repository contains a docker compose set of containers which are needed to run the Kong gateway locally. The
included containers are:

- **Kong Gateway** ( localhost:8000 / localhost:8001 )
- **Konga GUI** ( localhost:1337 )
- **Postgres 11** 

## Setup

Please run these migrations first:

```bash
$ docker compose run --rm migrations
```

### Run stack

After migrations have finished run with:

```bash
$ docker compose up -d
```

### Kong gateway setup

Kong services / routes and plugins needs to be assigned through the GUI by Konga.
Please setup Konga (Kong GUI):

- Open [Konga GUI](http://localhost:1337) in browser
- Go to `Snapshots` and select `details` for `snapshot`
- Click on `Restore`, select all subjects and restore import, repeat this twice!
- Verify all routes and services are imported

At default a few Kong services / routes and plugins are assigned.

```
localhost:8000/auth => host.docker.internal:9100
localhost:8000/geo => host.docker.internal:9200
```

`host.docker.internal` routes to the host machine, so we can add any service that is locally running.
