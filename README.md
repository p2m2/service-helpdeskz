# service-helpdeskz
[![Docker Pulls](https://badgen.net/docker/pulls/inraep2m2/service-helpdeskz?icon=docker&label=pulls)](https://hub.docker.com/r/inraep2m2/service-helpdeskz/)
[![CircleCI](https://circleci.com/gh/p2m2/service-helpdeskz.svg?style=shield)](https://circleci.com/gh/p2m2/service-helpdeskz)

inherits [helpdeskz-alpine](https://github.com/lakuapik/helpdeskz-alpine) repository.

### Running the image

```sh
# run mysql container
$ docker run \
    --name helpdeskz-mysql \
    -p 3306:3306 \
    -e MYSQL_DATABASE=helpdeskz \
    -e MYSQL_ROOT_PASSWORD=password \
    -d \
    mysql:8.0

# run helpdeskz container
$ docker run \
    --name helpdeskz-app \
    -p 80:80 \
    -v $(pwd)/Helpdesk.php:/var/www/html/hdz/app/Config/Helpdesk.php \
    --link helpdeskz-mysql:mysql \
    -d \
    p2m2/service-helpdeskz:latest

# visit http://localhost/install
```

