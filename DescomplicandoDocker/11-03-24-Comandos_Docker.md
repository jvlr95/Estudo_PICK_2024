Claro, aqui está a lista de comandos reescrita para melhor legibilidade:

**Subindo imagem ubuntu:latest com nome teste:**
   ```bash
   docker container run --name teste -it ubuntu:latest
   ```
**Comandos básicos:**
   ```bash
   docker container ls -a
   docker container stop
   docker container start
   docker container attach
   docker container rm
   ```
**Imprimir detalhes do container:**
   ```bash
   docker image inspect $CONTAINER
   ```
**Exibir estatísticas de uso de recursos de todos os containers em execução:**
   ```bash
   docker container stats
   ```
**Comando status sem ser dinâmico:**
   ```bash
   docker container status --no-stream
   ```
**Exibir os processos em execução dentro do container:**
   ```bash
   docker container top $CONTAINER
   ```
**Verificar logs de um container Docker:**
   ```bash
   docker container logs $CONTAINER
   ```
**Apagar todos os containers parados:**
   ```bash
   docker container prune -f
   ```
**Usar o comando --detach para rodar um container em segundo plano:**
   ```bash
   docker container run -d --name mywebserver nginx:latest
   ```
**Usar o comando exec para acessar o shell de um container em execução:**
   ```bash
   docker exec -ti mywebservice bash
   ```
