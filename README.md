# Reused-Modules
Reuse code for all type of project (Golang-Backend, NextJs-Frontend, or others ...)

## Start
```
mkdir -p ~/app
cd ~/app
git clone https://github.com/reused-modules/reused-modules.git
cd reused-modules
git clone https://github.com/reused-modules/reused-modules-api.git
<!-- git clone https://github.com/reused-modules/reused-modules-graphql.git -->
git clone https://github.com/reused-modules/reused-modules-front.git
git clone https://github.com/reused-modules/reused-modules-cms.git
docker-compose up -d
```

## API
- Environment variables

```
cp .env.example .env
```
## API Request

| Endpoint        | HTTP Method           | Description       |
| --------------- | :---------------------: | :-----------------: |
| `/v1/accounts` | `POST`                | `Create accounts` |
| `/v1/accounts` | `GET`                 | `List accounts`   |
| `/v1/accounts/{{account_id}}/balance`   | `GET`                |    `Find balance account` |
| `/v1/transfers`| `POST`                | `Create transfer` |
| `/v1/transfers`| `GET`                 | `List transfers`  |
| `/v1/health`| `GET`                 | `Health check`  |

- #### Creating new account

`Request`
```bash
curl -i --request POST 'http://localhost:8080/v1/accounts' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name": "Test",
    "cpf": "070.910.584-24",
    "balance": 100
}'
```

`Response`
```json
{
    "id":"5cf59c6c-0047-4b13-a118-65878313e329",
    "name":"Test",
    "cpf":"070.910.584-24",
    "balance":1,
    "created_at":"2020-11-02T14:50:46Z"
}
```
- #### Listing accounts

`Request`
```bash
curl -i --request GET 'http://localhost:8080/v1/accounts'
```

`Response`
```json
[
    {
        "id": "5cf59c6c-0047-4b13-a118-65878313e329",
        "name": "Test",
        "cpf": "070.910.584-24",
        "balance": 1,
        "created_at": "2020-11-02T14:50:46Z"
    }
]
```

- #### Fetching account balance

`Request`
```bash
curl -i --request GET 'http://localhost:8080/v1/accounts/{{account_id}}/balance'
```

`Response`
```json
{
    "balance": 1
}
```

- #### Creating new transfer

`Request`
```bash
curl -i --request POST 'http://localhost:8080/v1/transfers' \
--header 'Content-Type: application/json' \
--data-raw '{
	"account_origin_id": "{{account_id}}",
	"account_destination_id": "{{account_id}}",
	"amount": 100
}'
```

`Response`
```json
{
    "id": "b51cd6c7-a55c-491e-9140-91903fe66fa9",
    "account_origin_id": "{{account_id}}",
    "account_destination_id": "{{account_id}}",
    "amount": 1,
    "created_at": "2020-11-02T14:57:35Z"
}
```

- #### Listing transfers

`Request`
```bash
curl -i --request GET 'http://localhost:8080/v1/transfers'
```

`Response`
```json
[
    {
        "id": "b51cd6c7-a55c-491e-9140-91903fe66fa9",
        "account_origin_id": "{{account_id}}",
        "account_destination_id": "{{account_id}}",
        "amount": 1,
        "created_at": "2020-11-02T14:57:35Z"
    }
]
```
http://localhost:8080/

<!-- ## GRAPHQL
http://localhost:8000/ -->

## Front
http://localhost:3001/

## Cms
http://localhost:3002/

## DB
```
MYSQL_DATABASE: db
MYSQL_ROOT_PASSWORD: password
PORT: 33080:3306
```
