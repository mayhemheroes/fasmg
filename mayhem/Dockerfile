# Build Stage
FROM debian:bookworm-slim AS builder

RUN apt-get update && apt-get install -y --no-install-recommends fasm && rm -rf /var/lib/apt/lists/*

## Add source code to the build stage.
ADD . /src
WORKDIR /src

RUN cd core/source/linux/x64 && fasm -m 1000000 fasmg.asm /fasmg && chmod +x /fasmg

# Package Stage
FROM debian:bookworm-slim

COPY --from=builder /fasmg /
