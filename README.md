# hello_rails7_pg_redis
create a rails7 dev container

1. Generate your rails project in the dev container
   ```bash
   bundle exec rails new . --force -d=postgresql
   # or bundle exec rails new . --css=sass --javascript=esbuild --database=postgresql
   bundle config unset frozen
   bundle install
   ```
2. fix config/database.yml by adding `host`, `username` and `password` to the develoment section.
   ```yaml
   ...
   development:
     <<: *default
     database: try_rails7_development
     host: <%= ENV.fetch("DB_HOST") { "db" } %>
     username: <%= ENV.fetch("DB_USERNAME") { "postgres" } %>
     password: <%= ENV.fetch("DB_PASSWORD") { "password" } %>
   ...
   ```
