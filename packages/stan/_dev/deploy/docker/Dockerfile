ARG STAN_VERSION=0.15.1
FROM nats-streaming:$STAN_VERSION

# build stage
FROM golang:1.20.2-alpine3.17 AS build-env
RUN apk --no-cache add build-base git mercurial gcc
RUN go install github.com/nats-io/stan.go/examples/stan-bench@v0.5.2

# create an enhanced container with nc command available since nats is based
# on scratch image making healthcheck impossible
FROM alpine:3.17
RUN apk add --no-cache --upgrade bash
COPY --from=0 nats-streaming-server /nats-streaming-server
COPY --from=build-env /go/bin/stan-bench /stan-bench
# Expose client, management, and cluster ports
EXPOSE 4222 8222
ADD healthcheck.sh /healthcheck.sh
RUN ["chmod", "+x", "/healthcheck.sh"]
ADD run.sh /run.sh

# Healthcheck waits until channels have been created by the benchmark that runs inside
HEALTHCHECK --interval=1s --retries=100 CMD /healthcheck.sh

# Run with default memory based store
ENTRYPOINT ["/run.sh"]
