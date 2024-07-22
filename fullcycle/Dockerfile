FROM golang:latest AS builder

WORKDIR /app

COPY go.mod ./

RUN go mod download

COPY . .

RUN CGO_ENABLED=0 GOOS=linux go build -o executavel

###

FROM scratch

COPY --from=builder /app/executavel /

ENTRYPOINT [ "/executavel" ]