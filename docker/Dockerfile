# o comando as faz com que o docker n importe confguracoes no contexto (no caso abaixo no builder)  sendo assim a importacao do golang nao vai para iamagen, e sera usada somente no run do container 
FROM golang:1.15 as builder 
WORKDIR /go/src/fullcycle

COPY . .

RUN GOOS=linux go build -ldflags="-s -w"
RUN ls -la

FROM scratch 
WORKDIR /go/src/fullcycle
COPY --from=builder /go/src/fullcycle/fullcycle .

CMD ["./fullcycle"] 