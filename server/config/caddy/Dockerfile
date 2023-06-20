FROM caddy:builder-alpine AS builder
RUN xcaddy build \
    --with github.com/caddy-dns/route53@v1.3.3

FROM caddy:alpine
COPY --from=builder /usr/bin/caddy /usr/bin/caddy
