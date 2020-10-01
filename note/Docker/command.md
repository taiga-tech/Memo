
```
docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                               NAMES
0857ffa46199        e691f52c12cd        "entrypoint.sh bash …"   17 minutes ago      Up 14 minutes       0.0.0.0:3000->3000/tcp              smartorder_web_1
e07641928e4b        mysql:8.0           "docker-entrypoint.s…"   17 minutes ago      Up 14 minutes       33060/tcp, 0.0.0.0:4306->3306/tcp   smartorder_db_1
```

docker exec -it 0857ffa46199 bash

docker-compose run --rm web ~


docker system df -v

イメージ確認
docker image ls

キャッシュクリア

docker system prune

WARNING! This will remove:
  - all stopped containers
  - all networks not used by at least one container
  - all dangling images
  - all dangling build cache
