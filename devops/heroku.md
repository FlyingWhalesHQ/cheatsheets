---
layout: default
title: Heroku
parent: Devops
---

# Heroku Cheatsheet

---

## Basic

Create a new app

```sh
# generate random app name
heroku create

# specify app name
heroku create foo
```

Link a folder with an existing Heroku app:

```sh
heroku git:remote -a project
```

Different ways of running a heroku command with a particular app

```sh
# using git remote name
heroku command --remote remote_name
heroku command -r remote_name

# using app name
heroku command --app app_name
heroku command -a app_name
```

## Logs

- [https://devcenter.heroku.com/articles/logging](https://devcenter.heroku.com/articles/logging)

Log types and filters:

```
App logs: --source app
System logs: --source heroku
API logs: --source heroku --dyno api
```

Log format:

```sh
timestamp source[dyno]: message

# example
2010-09-16T15:13:46.677020+00:00 app[web.1]: Processing PostController#list (for 208.39.138.12 at 2010-09-16 15:13:46) [GET]
2010-09-16T15:13:46.677023+00:00 app[web.1]: Rendering template within layouts/application
2010-09-16T15:13:46.677902+00:00 app[web.1]: Rendering post/list
2010-09-16T15:13:46.678990+00:00 app[web.1]: Rendered includes/_header (0.1ms)
2010-09-16T15:13:46.698234+00:00 app[web.1]: Completed in 74ms (View: 31, DB: 40) | 200 OK [http://myapp.heroku.com/]
2010-09-16T15:13:46.723498+00:00 heroku[router]: at=info method=GET path="/posts" host=myapp.herokuapp.com" fwd="204.204.204.204" dyno=web.1 connect=1ms service=18ms status=200 bytes=975
2010-09-16T15:13:47.893472+00:00 app[worker.1]: 2 jobs processed at 16.6761 j/s, 0 failed ...
```

Commands:

```sh
# retrieve logs, 100 lines
heroku logs

# specify number of lines retrieved [--num / -n] max 1500
heroku logs -n 200

# get realtime logs [--tail / -t]
heroku logs --tail
```

## Postgresql

- [https://devcenter.heroku.com/articles/heroku-postgres-backups](https://devcenter.heroku.com/articles/heroku-postgres-backups)
- [https://devcenter.heroku.com/articles/heroku-postgres-import-export](https://devcenter.heroku.com/articles/heroku-postgres-import-export)

Common commands

```sh
# list backups
heroku pg:backups

# create a back up
heroku pg:backups:capture

# cancel backup
heroku pg:backups:cancel

# download latest backup
heroku pg:backups:download

# import backup to local database
pg_restore --verbose --clean --no-acl --no-owner -h localhost -U myuser -d mydb latest.dump
```

## Domains

- [https://devcenter.heroku.com/articles/custom-domains](https://devcenter.heroku.com/articles/custom-domains)

```sh
# list domains
heroku domains

# add domain
heroku domains:add www.example.com

# remove domain
heroku domains:remove www.example.com
```

## Maintenance mode

- [https://devcenter.heroku.com/articles/maintenance-mode](https://devcenter.heroku.com/articles/maintenance-mode)

```sh
heroku maintenance:on   # Enable maintenance mode
heroku maintenance:off  # Disable maintenance mode
heroku maintenance      # Check maintenance status
```
