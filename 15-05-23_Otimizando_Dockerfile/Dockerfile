# Estágio de construção
FROM alpine:3.15.9 AS builder
RUN apk update && apk add git --no-cache
RUN git clone https://github.com/badtuxx/giropops-senhas.git
WORKDIR /giropops-senhas
RUN apk update && apk add redis py-pip --no-cache && pip install --no-cache-dir -r requirements.txt
RUN pip install Flask werkzeug===2.2.2

# Estágio final
FROM alpine:3.15.9
RUN apk add --no-cache python3 py3-flask py3-redis
COPY --from=builder /giropops-senhas /giropops-senhas
WORKDIR /giropops-senhas
ENTRYPOINT ["flask", "run", "--host=0.0.0.0"]

