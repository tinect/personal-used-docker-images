FROM cgr.dev/chainguard/wolfi-base AS caddy_builder
RUN apk add --no-cache xcaddy go
RUN xcaddy build \
    --with github.com/caddy-dns/hetzner

# kills StackTrace, among other things
RUN strip --strip-all caddy

FROM cgr.dev/chainguard/static:latest
COPY --from=caddy_builder /caddy /usr/bin/caddy

ENV XDG_CONFIG_HOME /config
ENV XDG_DATA_HOME /data
CMD [ "/usr/bin/caddy", "run", "--config", "/etc/caddy/Caddyfile" ]
