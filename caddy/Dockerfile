#a6b0bdfda291f9d585e5882aefee2b705b32d87e6b4b8cc876f99e17394c2a2a
FROM cgr.dev/chainguard/wolfi-base AS caddy_builder
RUN apk add --no-cache xcaddy go git

# see https://github.com/caddy-dns/hetzner/issues/14#issuecomment-2888331388
RUN git clone https://github.com/Kugelschieber/caddy-dns-hetzner.git /fork
RUN git clone https://github.com/Kugelschieber/libdns-hetzner.git /fork-libdns && cd /fork-libdns && git checkout libdns-v1

RUN xcaddy build \
    --with github.com/caddy-dns/hetzner \
    --replace github.com/caddy-dns/hetzner=/fork \
    --replace github.com/libdns/hetzner=/fork-libdns

# kills StackTrace, among other things
RUN strip --strip-all caddy

FROM cgr.dev/chainguard/static:latest
COPY --from=caddy_builder /caddy /usr/bin/caddy

ENV XDG_CONFIG_HOME /config
ENV XDG_DATA_HOME /data
CMD [ "/usr/bin/caddy", "run", "--config", "/etc/caddy/Caddyfile" ]
