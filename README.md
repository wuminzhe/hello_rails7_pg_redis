# hello_rails7_pg_redis
create a rails7 dev container

1. Generate your rails project in the dev container
   ```bash
   bundle exec rails new . --force -d=postgresql
   # or bundle exec rails new . --css=sass --javascript=esbuild --database=postgresql
   bundle config unset frozen
   bundle install
   ```
