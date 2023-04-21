# hello_rails7_pg_redis
create a rails7 dev container

1. Generate your rails project in the dev container
   ```
   bundle exec rails new . --force -d=postgresql
   bundle config unset frozen
   bundle install
   ```
