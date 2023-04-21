# hello_rails7_pg_redis
A github template to create a rails7 dev container.

0. create a project from this template. for example: try_rails7
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
3. run your app in the container.
   ```bash
   bundle exec rails s -p 3000 -b '0.0.0.0'
   ```
4. now, everything is ready.
