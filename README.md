# base-app-nginx-sockets
rails6+nginx1.16(ソケット通信)

`docker-compose build`
`docker-compose run app bash`
`rails new . --force --database=mysql`


database.yml変更
```
default: &default
  adapter: mysql2
  encoding: utf8mb4
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: root
  password: root
  host: db

development:
  <<: *default
  database: app_development

test:
  <<: *default
  database: app_test

production:
  <<: *default
  database: app_production
  username: root
  password: root

```
`rails db:create`
`rails db:migrate`

localhostへ接続


productionモード ＝＞

`docker-compose run app bash`
`rails g controller home index`
`rails db:create`
`rails db:migrate`

config/routes.rb変更
```
Rails.application.routes.draw do
  root to: 'home/index'
end
```

`docker-compose build`
`docker-compose up`
