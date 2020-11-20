# Tor Buildpack for Heroku

This buildpack sets up a Local Tor client for your app on Heroku.

## Setup

Create a Heroku app as normal, with any buildpacks you typically use.
If you have a Go app, for instance, deploy it as normal.

Then:

```bash
$ heroku buildpacks:add https://github.com/talvasconcelos/heroku-buildpack-tor-service.git
```

With the buildpack installed, you'll need to modify your Procfile such that
the hidden service will be setup when the app runs.

```Procfile
web: hide <cmd you'd normally run>
```

While `web` works just fine, so too will any other process type. Use `web`
if you want the app to be accessible generally, as well as over Tor. Use
`<any other type>`, to avoid Heroku's router routing to your app like so:
```
foo: PORT=9999 hide <cmd you'd normally run>
```
