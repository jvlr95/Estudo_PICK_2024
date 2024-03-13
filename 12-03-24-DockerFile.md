# Dockerfile: Um Guia Rápido

Um Dockerfile é um arquivo de configuração usado para construir uma imagem Docker. Ele contém instruções que o Docker usa para criar a imagem camada por camada. Aqui está um exemplo básico de Dockerfile e suas principais instruções:

```Dockerfile
# Escolhe a imagem base
FROM ubuntu:20.04

# Metadados da imagem
LABEL maintainer="jvitor.lr@testeteste.com"

# Executa comandos durante a construção da imagem
RUN apt-get update && apt-get install nginx curl -y && rm -rf /var/lib/apt/lists/*

# Expõe uma porta para comunicação com o exterior
EXPOSE 80

# Define o diretório de trabalho dentro do contêiner
WORKDIR /root

# Adiciona um arquivo ou URL ao sistema de arquivos do contêiner
ADD https://github.com/prometheus/node_exporter/releases/download/v1.6.0/node_exporter-1.6.0.linux-amd64.tar.gz .

# Executa comandos para configurar a aplicação
RUN tar -xzf node_exporter-1.6.0.linux-amd64.tar.gz && rm node_exporter-1.6.0.linux-amd64.tar.gz

# Copia arquivos do host para o contêiner
COPY index.html /var/www/html/

# Define uma variável de ambiente
ENV APP_VERSION 1.0.0

# Define o comando padrão a ser executado quando o contêiner for iniciado
ENTRYPOINT ["nginx"]

# Argumentos padrão para o ENTRYPOINT
CMD ["-g", "daemon off;"]

# Verifica o estado da aplicação dentro do contêiner
HEALTHCHECK --timeout=2s CMD curl -f localhost || exit 1
```

- `FROM`: Especifica a imagem base que você deseja usar.
- `LABEL`: Define metadados para a imagem, como o mantenedor.
- `RUN`: Executa comandos durante a construção da imagem.
- `EXPOSE`: Expõe portas do contêiner para comunicação com o host.
- `WORKDIR`: Define o diretório de trabalho dentro do contêiner.
- `ADD`: Adiciona arquivos ou URLs ao sistema de arquivos do contêiner.
- `COPY`: Copia arquivos do host para o contêiner.
- `ENV`: Define variáveis de ambiente dentro do contêiner.
- `ENTRYPOINT`: Define o comando padrão a ser executado quando o contêiner for iniciado.
- `CMD`: Fornece argumentos padrão para o `ENTRYPOINT`.
- `HEALTHCHECK`: Verifica o estado da aplicação dentro do contêiner.

