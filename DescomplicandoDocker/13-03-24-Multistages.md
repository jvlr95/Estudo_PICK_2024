### Multistage Dockerfile

O Docker suporta a construção de imagens Docker em múltiplas etapas, permitindo que você crie imagens mais leves e eficientes. O multistage build é útil quando você precisa compilar código-fonte ou realizar outras tarefas durante a construção da imagem, mas não quer incluir essas dependências na imagem final.

#### Como funciona:

1. **Construção em etapas**: O Dockerfile é dividido em várias etapas, cada uma com suas próprias instruções e contexto de construção. Cada etapa pode copiar arquivos ou executar comandos, resultando em uma imagem intermediária.

2. **Imagem final**: A última etapa do Dockerfile especifica a imagem final que será criada a partir dos artefatos das etapas anteriores. A imagem final geralmente é menor e contém apenas o necessário para executar a aplicação.

#### Exemplo de Dockerfile multistage:

```Dockerfile
# Etapa 1: Compilar o código-fonte
FROM golang:1.18 AS builder
WORKDIR /app
COPY . .
RUN go mod download
RUN go build -o myapp

# Etapa 2: Criar a imagem final
FROM alpine:latest
RUN apk --no-cache add ca-certificates
WORKDIR /root/
COPY --from=builder /app/myapp .
CMD ["./myapp"]
```

Neste exemplo, a primeira etapa compila o código Go e cria o executável `myapp`. A segunda etapa usa uma imagem Alpine Linux mínima como base e copia o executável `myapp` da primeira etapa, resultando em uma imagem final leve e pronta para uso.

#### Benefícios:

- Redução do tamanho da imagem: A imagem final contém apenas os artefatos necessários para executar a aplicação, sem as dependências de compilação.
- Maior segurança: Menos componentes na imagem reduzem a superfície de ataque e a vulnerabilidade.
- Eficiência no CI/CD: Menos etapas de construção e imagens menores resultam em tempos de construção mais rápidos e implantações mais rápidas.

	O multistage build é uma técnica poderosa para otimizar o tamanho e o desempenho das suas imagens Docker, especialmente para aplicações complexas com muitas dependências de compilação.
