# Vi kör en multistage Dockerfile idag, på så sätt minimerar vi storleken på image som körs.

# Stage 1, Vi använder den officiella Golang imagen för kompilera vå Go app. Sedan kopieras källkoden till vår container och exekveras av vår "go build" kommando.
FROM golang:1.17-alpine as builder
WORKDIR /app
COPY . .
RUN go build-o main .

# Steg 2, här bygger vi en minimal Alpine image som i sin tur använder den kompilerade koden från föregående build stage.
FROM alpine:latest
WORKDIR /root/
COPY --from=builder /app/main .
CMD ["./main"]
