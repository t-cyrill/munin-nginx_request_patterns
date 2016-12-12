munin-nginx\_request\_patterns
========================

Munin plugin for nginx request patterns

Usage
----------------

munin-nginx\_request\_patterns plugin needs File::ReadBackwards modules.

```
sudo cpanm File::ReadBackwards
```

And then,

```
ln -s nginx_request_patterns /etc/munin/plugins/nginx_request_patterns
```

Configration
----------------

### logfile

Log file path. You can set multi-logfile using camma.

* ie. /var/log/nginx/access.log,/var/log/nginx/access.log.1

### loglimit

Read limit for "tail log". Default value is 1000.

* ie. 1000

### log\_format

Log file format "tsv" or "ltsv".

### log\_method\_idx log\_uri\_idx

HTTP methods and URI column in Log.

### log\_match

Exclude unmatched line.
It is useful filter specific line.

### log\_exclude

Exclude matched line.
It is useful filter specific line.

### patterns

Note: Automatic add `.*` last.

```
env.patterns GET /api/,POST /api/,GET /,POST /
```

### Example

```
[nginx_request_patterns]
    env.logfile /var/log/nginx/access.log
    env.loglimit 1000
    env.log_format ltsv
    env.log_method_idx 9
    env.log_uri_idx 10
    env.exclude ([^\t]+(\.png|\.css|\.js$|\.jpg|\.ico|\.svg|\.gif)\t)
    env.patterns GET /api/,POST /api/,GET /,POST /
```
