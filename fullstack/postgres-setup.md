running on Docker is the easiest PostgreSQL setup:
- docker run --name *** -e POSTGRES_PASSWORD=*** -p 5431:5432 -d postgres
check containers:
- docker ps -a
interact:
- docker exec -it onchain-stripe-db psql -U postgres