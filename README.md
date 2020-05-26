[Heroku lokal web](https://gist.github.com/hone/24b06869b4c1eca701f9)
1.Необходимо залогинется
2.Запустить npm run build
3.Запустить heroku local web


##Процесс установки
```blade
npm install express --save
регестрируемся на Heroku создаем новое App
Устанавливаем heroku cli
Так же должен быть установлен Git
heroku login
Переходим в heroku в раздел deploy и выполняем все команды
git init
....
git commit -am "update files"
git push heroku master
Далее переходим на Vue CLI
Создаем файл static.json
{
  "root": "dist",
  "clean_urls": true,
  "routes": {
    "/**": "index.html"
  }
}
git add static.json
git commit -m "add static configuration"
Deploy to Heroku
heroku login
heroku create
heroku buildpacks:add heroku/nodejs
heroku buildpacks:add https://github.com/heroku/heroku-buildpack-static
heroku buildpacks:add heroku-community/nginx - до конца не проверено
git push heroku master

Если надо очистить heroku buildpacks
heroku buildpacks:clear
heroku buildpacks:remove heroku/nodejs - удаляет конкретный пакет https://devcenter.heroku.com/articles/buildpacks
https://devcenter.heroku.com/articles/buildpacks#officially-supported-buildpacks
```
[Vue CLI](https://cli.vuejs.org/guide/deployment.html#heroku)

##Можно так по-быстрому
```blade
git init
heroku login
heroku create
heroku buildpacks:add heroku/nodejs
heroku buildpacks:add https://github.com/heroku/heroku-buildpack-static
git add static.json
git commit -m "add static configuration"
git push heroku master
```


# vue-nodejs-mysql-nginx-heroku

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
