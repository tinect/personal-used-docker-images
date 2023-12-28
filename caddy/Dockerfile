# Build Caddy modules
FROM caddy:2.7.6-builder-alpine AS caddy_builder
RUN xcaddy build \
    --with github.com/caddy-dns/hetzner

# Caddy image
FROM caddy:2.7.6-alpine AS caddy
COPY --from=caddy_builder /usr/bin/caddy /usr/bin/caddy