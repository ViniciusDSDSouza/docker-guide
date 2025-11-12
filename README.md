# 🐳 Docker & Docker Compose – Guia Rápido

## 📦 **1. Buildar e subir containers**

```bash
# Derruba todos os containers definidos no arquivo Compose
docker compose -f docker-compose.yml down

# Rebuilda as imagens sem usar cache
docker compose -f docker-compose.yml build --no-cache

# Sobe os containers em segundo plano (modo detached)
docker compose -f docker-compose.yml up -d
```

🔹 O arquivo `docker-compose.yml` define todos os serviços do projeto (ex: app, db, redis).
🔹 O `--no-cache` força o Docker a não reutilizar camadas antigas da imagem.

---

## 🧭 **2. Acessar um container**

```bash
# Abre um terminal dentro do container
docker exec -it nome-do-container sh
```

💡 Use `bash` no lugar de `sh` se o container tiver Bash instalado.

---

## 📜 **3. Visualizar logs**

```bash
# Ver logs do container
docker logs nome-do-container

# Ver logs em tempo real (follow)
docker logs -f nome-do-container
```

---

## 🔁 **4. Reiniciar containers**

```bash
# Reinicia um container
docker restart nome-do-container
```

---

## 🧹 **5. Limpar imagens e containers antigos**

```bash
# Remove containers parados
docker container prune

# Remove imagens não utilizadas
docker image prune

# Limpa tudo (containers, imagens, volumes e cache)
docker system prune -a
```

⚠️ O `-a` apaga todas as imagens não usadas — use com cuidado.

---

## 🧱 **6. Gerenciar imagens**

```bash
# Listar imagens locais
docker images

# Apagar uma imagem específica
docker rmi nome-da-imagem
```

---

## 🧩 **7. Gerenciar containers**

```bash
# Listar containers em execução
docker ps

# Listar todos (inclusive parados)
docker ps -a

# Parar um container
docker stop nome-do-container

# Iniciar um container parado
docker start nome-do-container

# Remover um container
docker rm nome-do-container
```

---

## 🐙 **8. Executar comandos dentro do container**

```bash
# Instalar pacotes, rodar scripts, etc.
docker exec nome-do-container npm install
docker exec nome-do-container node script.js
docker exec nome-do-container ls /app
```

---

## 🚀 **9. Atalho (Rebuild + Up em um comando)**

Crie um script no seu `package.json`:

```json
"scripts": {
  "docker:rebuild": "docker compose -f docker-compose.yml down && docker compose -f docker-compose.yml build --no-cache && docker compose -f docker-compose.yml up -d"
}
```

Depois é só rodar:

```bash
npm run docker:rebuild
```

---

## 🧾 **Resumo rápido**

| Ação                    | Comando                                                 |
| ----------------------- | ------------------------------------------------------- |
| Subir containers        | `docker compose -f docker-compose.yml up -d`            |
| Parar containers        | `docker compose -f docker-compose.yml down`             |
| Rebuildar imagens       | `docker compose -f docker-compose.yml build --no-cache` |
| Entrar no container     | `docker exec -it nome-do-container sh`                  |
| Ver logs                | `docker logs -f nome-do-container`                      |
| Listar containers       | `docker ps`                                             |
| Limpar cache de imagens | `docker system prune -a`                                |

---

## 🧠 **Conceitos básicos**

| Conceito               | Descrição                                                              |
| ---------------------- | ---------------------------------------------------------------------- |
| **Imagem**             | É o "molde" — contém o sistema, dependências e código.                 |
| **Container**          | É uma instância em execução da imagem.                                 |
| **Volume**             | Permite salvar dados fora do container (para não perder ao reiniciar). |
| **Dockerfile**         | Script com as instruções para construir a imagem.                      |
| **docker-compose.yml** | Define e orquestra vários containers de um projeto.                    |
