A Heroku buildpack to add [`jq`](https://github.com/stedolan/jq) using [`Onigmo regex library`](https://github.com/k-takata/Onigmo) to any build or Dyno.

### Usage
``` bash
$ heroku buildpacks:add --index 1 https://github.com/szgupta/heroku-buildpack-jq.git --app <APP_NAME>
```
Note that you'll want to add the `jq` buildpack *before* any buildpack that relies on `libjq` (e.g. [`ruby-jq`](https://github.com/winebarrel/ruby-jq)). Supplying `--index 1` as an option will guarantee this.

If using with `ruby-jq`, ensure Ruby doesn't compile its own libjq:
```
RUBYJQ_USE_SYSTEM_LIBRARIES=yes gem install ruby-jq
```
