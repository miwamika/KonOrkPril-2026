# Лабораторная работа №1. Знакомство с Docker

**Студент:** Арзуманьян София Артемовна  
**ИСУ:** 465041  
**Порт:** 5471  
**Префикс:** arzumanian

## Инструкция по воспроизведению

### Этап 1. Верификация окружения
```cmd
docker version --format "Client: {{.Client.Version}}, Server: {{.Server.Version}}"
docker info --format "{{.OSType}}/{{.Architecture}}"
docker system df --format "table {{.Type}}\t{{.TotalCount}}\t{{.Active}}\t{{.Size}}"
```
### Этап 2. Базовые образы
```cmd
docker run --rm hello-world
docker run --rm alpine:3.18 cat /etc/os-release
docker run -d --name arzumanian-alpine-1 alpine:3.18 sleep 300
docker run -d --name arzumanian-alpine-2 alpine:3.18 sh -c "echo 'Hello' && sleep 300"
docker ps --filter "name=arzumanian-alpine"
```
### Этап 3. Жизненный цикл
```cmd
docker create --name arzumanian-nginx nginx:alpine
docker start arzumanian-nginx
docker stop arzumanian-nginx
docker restart arzumanian-nginx
docker kill arzumanian-nginx
docker ps -a --filter "name=arzumanian-nginx"
docker rm arzumanian-nginx
```
### Этап 4. Диагностика PostgreSQL
```cmd
docker run -d --name arzumanian-pg-broken -p 5471:5432 postgres:15
docker logs arzumanian-pg-broken

docker run -d --name arzumanian-pg-fixed -e POSTGRES_PASSWORD=Pass_5471 -e POSTGRES_USER=user_465041 -p 5471:5432 postgres:15
docker exec arzumanian-pg-fixed psql -U user_465041 -c "SELECT version();"
```
