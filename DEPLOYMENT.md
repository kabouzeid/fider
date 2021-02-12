# Deploy

## Installed packages
- go
- nodejs

```bash
# build deps
go get github.com/joho/godotenv/cmd/godotenv

# build server
go build

# build UI
npm install
env NODE_ENV=production npx webpack -p

# run migrations & serve
godotenv -f .env ./fider migrate && godotenv -f .env ./fider
```
