
docker network create back-tier

```
docker run -d -p 5432:5432 --name=postgresdb --network=back-tier \
-e POSTGRES_USER="postgres" \
-e POSTGRES_PASSWORD="admin123" \
-v postgress-volume:/var/lib/postgresql/data \
postgres:latest

```

docker run -it -d -p 80:80 --network=back-tier  --name=ui saurabhd2106/frontend-3tier

docker run -it -d -p 81:80 --network=back-tier -e "ConnectionStrings__Basic3Tier: Host=basic-3tier-postgres;Port=5432;Database=basic3tier;Username=postgres;Password=admin123" --name=backend saurabh2106/backend-3tier