# Distroless 
* Subir containers sem alguma distribuição alocada, apenas a linguagem
** no-cache-dir --> não armazena arquivos
** Dockerfile aplicacao giropops-senhas
---

```bash
FROM python:3.11

WORKDIR /app
COPY . .
RUN pip install --no-cache-dir -r requeriments.txt
EXPOSE 5000
CMD ["flask", "run","--host=0.0.0.0"]

```

---
# Buildar e executar a img:

** Build:
	```bash
	docker image build -t giropops-senhas:1.0 .
	```

** Executar imagem:
	```bash
	docker run -d --name girpops-senhas -p 5000:5000 giropops-senhas:1.0
	```
** Verificando logs:
	```bash
	docker container logs giropops-senhas
	```


