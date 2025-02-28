# DevOps


## Chapters
1. How to seperate you credential in .env file and use it to docker compose file
[here](/env-with-docker-compose/)


`.env`

```bash
POSTGRES_USER=abhi
POSTGRES_PASSWORD=merapassword
POSTGRES_DB=codebhaiya
```

`docker-compose.yml`
```yml
name: "learning"

services:
  db:
    image: postgres:alpine
    container_name: mydb
    env_file:
      - .env
    environment:
      - POSTGRES_USER=${POSTGRES_USER}
      - POSTGRES_PASSWORD=${POSTGRES_PASSWORD}
      - POSTGRES_DB=${POSTGRES_DB}
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data
volumes:
  postgres_data:
```