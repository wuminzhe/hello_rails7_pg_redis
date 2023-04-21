# hello_rails7_pg_redis
create a rails7 dev container

1. Generate your rails project in the dev container
   ```bash
   bundle exec rails new . --force -d=postgresql
   # or bundle exec rails new . --css=sass --javascript=esbuild --database=postgresql
   bundle config unset frozen
   bundle install
   ```
2. fix config/database.yml by adding a host to the develoment config.
   ```yaml
   ...
   development:
     <<: *default
     host: <%= ENV.fetch("DB_HOST") { "db" } %>
     database: try_rails7_development
   ...
   ```
