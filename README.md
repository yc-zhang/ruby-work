#### This is a sample to show you how to deploy unicorn and nginx

Clone this repo to local, then run the following:

```shell
$ mkdir log
$ mkdir tmp
$ mkdir tmp/pids
$ mkdir tmp/sockets
```
Change `path/to/app` to this app folder in `config.rb`

Then update your nginx config file and please refer to `nginx/config/sample.conf`

After that, prepare ruby gems:

```shell
$ bundle install
```

Hmm... it seems you could start unicorn:

```shell
$ unicorn -c config.rb -E development -D
```

Check the pids file and Unix Domain Socket file at `tmp/` folder

Then start nginx:
```shell
$ nginx
```

See the magic in your browser with url http://127.0.0.1:8888

Stop the unicorn and nginx by the following:

```shell
$ nginx -s stop
$ cat tmp/pids/unicorn.pid | xargs kill -QUIT
```
 
Reference:
http://sirupsen.com/setting-up-unicorn-with-nginx/
http://recipes.sinatrarb.com/p/deployment/nginx_proxied_to_unicorn
