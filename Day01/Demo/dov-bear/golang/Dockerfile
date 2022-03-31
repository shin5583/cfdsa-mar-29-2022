FROM golang:1.17 AS builder

ARG APP_DIR=/app

WORKDIR ${APP_DIR}

ADD main.go .
ADD go.mod .
ADD go.sum .


#/app/main
RUN go build -o main main.go

FROM golang:1.17

ARG APP_DIR=/app

WORKDIR ${APP_DIR}

COPY --from=builder ${APP_DIR} .
ADD public public
ADD templates templates

ENV INSTANCE_NAME=GoLang
ENV INSTANCE_HASH=GoLangHASH
ENV PORT=3000

EXPOSE ${PORT}

HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 \
    CMD curl http://localhost:${PORT}/htealthz || exit 1


ENTRYPOINT ["main.go"]