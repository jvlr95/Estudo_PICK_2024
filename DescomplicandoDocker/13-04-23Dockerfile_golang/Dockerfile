FROM golang:1.18 as build
WORKDIR /app
COPY . ./
RUN go mod init hello
RUN go build -o /app/hello

# Multistage dockerfile -- add imagem container alpine
FROM alpine:3.15.9
SHELL ["/bin/bash"]
COPY --from=build /app/hello /app/hello
ENV APP="hello_world"
ARG GIROPOPS="strigus"
VOLUME /app/dados
CMD ["/app/hello"]
