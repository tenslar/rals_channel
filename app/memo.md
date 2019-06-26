## run

```bash
docker image build -t test/laravel/app ./
docker container run --rm -t -v /Users/ralsspc013/dev/test_laravel/app:/home -p 55555:8000 test/laravel/app

curl localhost:55555

#<!doctype html>
#<html lang="en">
#    <head>
#        <meta charset="utf-8">
#        <meta name="viewport" content="width=device-width, initial-scale=1">
#
#        <title>Laravel</title>
# :
# :

```


