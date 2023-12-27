ARG CADDY_VERSION=2

# Build Caddy modules
FROM caddy:${CADDY_VERSION}-builder-alpine AS caddy_builder
RUN xcaddy build \
    --with github.com/caddy-dns/hetzner

# Caddy image
FROM caddy:${CADDY_VERSION}-alpine AS caddy
COPY --from=caddy_builder /usr/bin/caddy /usr/bin/caddy