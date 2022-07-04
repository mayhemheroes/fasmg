# Build Stage
FROM debian:buster as builder

RUN apt update && apt install -y fasm

## Add source code to the build stage.
ADD . /src
WORKDIR /src

RUN cd core/source/linux/x64 && fasm -m 1000000 fasmg.asm /fasmg && chmod +x /fasmg

# Package Stage
FROM debian:buster

COPY --from=builder /fasmg /
