FROM golang:1.19 AS build

WORKDIR /app

COPY main.go ./
COPY go.mod ./

RUN go build -o /server

FROM gcr.io/distroless/base-debian11

WORKDIR /

COPY --from=build /server /server

EXPOSE 8080

USER nonroot:nonroot

ENTRYPOINT [ "/server" ]