# hello_rails7_pg_redis

A template to create a rails 7 dev container.

0. create a repo from this template.
1. clone the repo to your local
2. start a dev container for your local repo.

   I tried 1. vscode, 2. neovim + [nvim-dev-container](https://github.com/esensar/nvim-dev-container). both are ok.
   
4. In your dev container

   1. `gem install rails -v 7.1.0.beta1`
    
      https://rubyonrails.org/2023/9/13/Rails-7-1-0-beta-1-has-been-released

   2. (optional) `service start cron` if you need crontab to work.

   3. Generate your rails project in the dev container.
      For example, the commands below will create a new Rails project using the Rails 7 default assets pipeline which is my favorite.

      ```bash
      # importmaps + propshaft (my prefer) 
      rails new . -a propshaft -d=postgresql

      # or, one of the following
      # * importmaps + sprockets
      rails new . -d=postgresql

      # * importmaps + sprockets + tailwind, https://techracho.bpsinc.jp/hachi8833/2022_02_17/115435
      rails new . --css tailwind -d=postgresql

      # * importmaps + propshaft + tailwind
      rails new . --css tailwind -a propshaft -d=postgresql

      # * (nodejs) esbuild + sprockets + tailwind
      rails new . --javascript esbuild --css tailwind -d=postgresql

      # * (nodejs) esbuild + propshaft + bootstrap
      rails new . --javascript esbuild --css bootstrap -a propshaft -d=postgresql
      ```

   4. fix config/database.yml by adding the `host`, `username` and `password` to the development section.

      ```yaml
      ...
      default: &default
         ...
         host: <%= ENV.fetch("DB_HOST") { "db" } %>
         username: <%= ENV.fetch("DB_USERNAME") { "postgres" } %>
         password: <%= ENV.fetch("DB_PASSWORD") { "password" } %>
      ...
      ```

      ```bash
      bundle exec rails db:create
      ```

   4. run your app in the container.

      ```bash

      ./bin/dev
      ```

5. now, everything is ready.
