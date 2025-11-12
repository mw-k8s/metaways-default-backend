# Metaways Default kubernetes Backend

based on https://github.com/kubernetes/ingress-nginx `images/custom-error-pages/rootfs`

Github workflow created with github copilot

## Features

- Lightweight nginx-based default backend
- Custom error pages (404, 50x)
- Multi-architecture Docker images (armv7, arm64/v8, amd64)
- Automated builds via GitHub Actions

## Docker Images

Images are automatically built and pushed to GitHub Container Registry:
- `ghcr.io/mw-k8s/metaways-default-backend:latest`
- `ghcr.io/mw-k8s/metaways-default-backend:<git-tag>` (when tagged)
- `ghcr.io/mw-k8s/metaways-default-backend:<commit-sha>` (when not tagged)

## Supported Architectures

- linux/arm/v7
- linux/arm64/v8
- linux/amd64

## Usage

Pull and run the latest image:

```bash
docker pull ghcr.io/mw-k8s/metaways-default-backend:latest
docker run -d -p 8080:8080 ghcr.io/mw-k8s/metaways-default-backend:latest
```

Visit http://localhost:8080 to see the default backend page.

## Development

### Building Locally

```bash
docker build -t metaways-default-backend .
```

### Running Locally

```bash
docker run -d -p 8080:8080 metaways-default-backend
```

## GitHub Actions Workflow

The repository includes a GitHub Actions workflow that:
- Triggers on pushes to main/master branches and on tags
- Uses Docker Buildx for multi-platform builds
- Authenticates with GitHub Container Registry
- Builds for multiple architectures in parallel
- Tags images based on git tags or commit SHA
- Pushes to ghcr.io/mw-k8s/metaways-default-backend
