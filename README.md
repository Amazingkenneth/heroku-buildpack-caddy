# Heroku Caddy Buildpack

Run [Caddy](https://caddyserver.com/) in Heroku.

Built according to Heroku's [buildpack API](https://devcenter.heroku.com/articles/buildpack-api).

## Quick Start

Get the `buildpack.tar.gz` download URL from [the latest release](https://github.com/thermondo/heroku-buildpack-caddy/releases/latest).
It should look something like:

```plaintext
https://github.com/thermondo/heroku-buildpack-caddy/releases/download/LATEST_VERSION_NUMBER/buildpack.tar.gz
```

Then run:

```bash
heroku buildpacks:add <the-buildpack-url>
```

Then in your app's [Procfile](https://devcenter.heroku.com/articles/procfile) add something like this:

```plaintext
web: caddy --config <your Caddyfile>
```

If you want to run a specific version of Caddy, set the `CADDY_RELEASE` environment variable on your
app as seen on [Caddy's GitHub releases](https://github.com/caddyserver/caddy/releases) (for
example: `v2.8.4`). Otherwise it will install the latest version of Caddy from GitHub.

🚨 _If you choose to use the latest version of Caddy from GitHub, and there's a new **MAJOR** Caddy
release, this buildpack will **abort the build** with a helpful log message telling you what to do
in this case: Either pin the release you want with `CADDY_RELEASE` or check this repo for updates
that support the latest major version._

## Developing

### Creating Releases

Go to [the release workflow](https://github.com/thermondo/heroku-buildpack-caddy/actions/workflows/release.yml)
and manually trigger a release. Specify an appropriate tag name using semantic versioning rules.

Then go to the newly created draft release on the [releases page](https://github.com/thermondo/heroku-buildpack-caddy/releases),
polish it up, and publish it.
