# Estudo sobre vulnerabilidades
## Day3

### Algumas ferramentas usadas para análise:

- **unshare**: Ferramenta para verificar vulnerabilidades em containers. Ela examina a vulnerabilidade "unshare" que afeta containers.

- **Docker Scout**: Ferramenta para verificar vulnerabilidades em containers Docker.
  - Instalação do scout, seguir passo a passo conforme documentação [aqui](https://docs.docker.com/scout/install/).

- Utilizando o CLI do scout:
  ```bash
  docker scout cves $IMAGE
  ```

- Mais informações: digitar `docker scout` e o aplicativo retorna o que é possível fazer.

- **Trivy**: Ferramenta para escanear e verificar vulnerabilidades em containers, retorna banco de dados com relatório geral e versões que fixaram vulnerabilidades.
  - Instalação do [Trivy](https://aquasecurity.github.io/trivy/v0.50/getting-started/installation/).

- Utilizando o CLI do Trivy:
  ```bash
  trivy imagem $IMAGE
  ```

