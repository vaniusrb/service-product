## Project to demonstrate product API service

### Pre-requisites

- Install `sqlx-client`

```
cargo install sqlx-cli
```

### Setup

Create `.env` file in the project root. Define something like this:

```
POSTGRES_PASSWORD = "password"
DATABASE_URL=postgres://vs-academy-product-postgres:password@127.0.0.1/product
```

Start database container:

```
docker-compose up
```

Create Postgres database:

```
sqlx database create
sqlx migrate run
```

### Future updates

Always when update the project (from git) should execute database modifications:

```
sqlx migrate run
```

### Execute the project

To execute project, using address 127.0.0.1:3000:

```
cargo run
```

### Project guideline

#### Database

- Table in singular name
- Primary key should be named `id` and has type `UUID`
- All tables should have field `created_at` with type `TIMESTAMP`
- SQL statements should be uppercase
- Tables and fields name should be lowercase and inside double quotes
- Date/time fields should be `TIMESTAMP`, without time zone
- Date/time fields consider UTC time

#### Rest API

- Endpoint in plural name
- Operations:

```
list    GET    api/products
create  POST   api/products/:id
read    GET    api/products/:id
update  PATCH  api/products/:id
delete  DELETE api/products/:id
```

### Maintenance

#### Changing database

- Execute `sqlx migrate add <migration_name>`
- Insert SQL statements in the .sql file
- Execute `sqlx migrate run`

#### Problem with route functions declaration

If you have some compiling problem defining function route it's possible declare this attribute on the function, to get better error:

```
#[debug_handler]
```
