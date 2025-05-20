FROM golang:1.20-alpine AS base

FROM base AS builder
WORKDIR /app

COPY . .
RUN go build -o bin/app ./main.go

FROM gcr.io/distroless/static-debian12 AS runner
COPY --from=builder /app/bin/app /app/bin/app 
EXPOSE 8080

ENTRYPOINT ["/app/bin/app"]
