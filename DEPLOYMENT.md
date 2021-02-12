# Deploy

## Environment
Create `.env` file.

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

# run migrations
godotenv -f .env ./fider migrate &&

# serve
godotenv -f .env ./fider
```

## Nginx

```nginx
location / {
    proxy_pass http://localhost:3000;
    proxy_pass_header Server;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_connect_timeout 3s;
    proxy_read_timeout 10s;
}
```

:warning: Important: `proxy_set_header X-Forwarded-Proto $scheme;`
