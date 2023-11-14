FROM golang:1.21 as builder


WORKDIR /app

RUN go mod init git.com/gugags6
RUN go mod tidy


RUN go mod download && go mod verify


COPY . /app
RUN CGO_ENABLED=0 GOOS=linux go build -o fullcycle main.go

FROM scratch

WORKDIR /app

COPY --from=builder /app/fullcycle ./

CMD ["./fullcycle"]


