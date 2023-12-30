FROM golang:1.14-alpine AS build

RUN mkdir -p /go/src/github.com/taniaduggal/taskk ~/.ssh && \
    apk add --no-cache git openssh-client make gcc libc-dev
WORKDIR /go/src/github.com/taniaduggal/taskk
COPY . .
RUN make build

FROM alpine:3
COPY --from=build /go/src/github.com/taniaduggal/taskk/article-server /bin/article-server
CMD /bin/article-server

