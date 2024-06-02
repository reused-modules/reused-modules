# Reused-Modules
Reuse code for all type of project (Golang-Backend, NextJs-Frontend, or others ...)

## Start
```
mkdir -p ~/app
cd ~/app
git clone https://github.com/PhanAnh1001/reused-modules.git
cd reused-modules
git clone https://github.com/PhanAnh1001/reused-modules-api.git
cd ./
docker-compose up db api
```

## API
### Url
http://localhost:8080/

### DB
MYSQL_DATABASE: db
MYSQL_ROOT_PASSWORD: password
PORT: 33061:3306
