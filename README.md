# Heroku Buildpack for Node.js

![nodesjs](https://cloud.githubusercontent.com/assets/51578/8882955/3f0c3980-3219-11e5-8666-bc9c926a7356.jpg)

This is the official [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for Node.js apps.

[![Build Status](https://travis-ci.org/heroku/heroku-buildpack-nodejs.svg)](https://travis-ci.org/heroku/heroku-buildpack-nodejs)

## Documentation

For more information about using this Node.js buildpack on Heroku, see these Dev Center articles:

- [Heroku Node.js Support](https://devcenter.heroku.com/articles/nodejs-support)
- [Getting Started with Node.js on Heroku](https://devcenter.heroku.com/articles/nodejs)

For more general information about buildpacks on Heroku:

- [Buildpacks](https://devcenter.heroku.com/articles/buildpacks)
- [Buildpack API](https://devcenter.heroku.com/articles/buildpack-api)

## Locking to a buildpack version

In production, you frequently want to lock all of your dependencies - including
buildpacks - to a specific version. That way, you can regularly update and
test them, upgrading with confidence.

First, find the version you want from
[the list of buildpack versions](https://github.com/heroku/heroku-buildpack-nodejs/releases).
Then, specify that version with `buildpacks:set`:

```
heroku buildpacks:set https://github.com/heroku/heroku-buildpack-nodejs#v83 -a my-app
```

If you have trouble upgrading to the latest version of the buildpack, please
open a support ticket at [help.heroku.com](https://help.heroku.com/) so we can assist.

### Chain Node with multiple buildpacks

This buildpack automatically exports node, npm, and any node_modules binaries
into the `$PATH` for easy use in subsequent buildpacks.

## Feedback

Having trouble? Dig it? Feature request?

- [help.heroku.com](https://help.heroku.com/)
- [@hunterloftis](http://twitter.com/hunterloftis)
- [github issues](https://github.com/heroku/heroku-buildpack-nodejs/issues)

## Hacking

To make changes to this buildpack, fork it on Github.
Push up changes to your fork, then create a new Heroku app to test it,
or configure an existing app to use your buildpack:

```
# Create a new Heroku app that uses your buildpack
heroku create --buildpack <your-github-url>

# Configure an existing Heroku app to use your buildpack
heroku buildpacks:set <your-github-url>

# You can also use a git branch!
heroku buildpacks:set <your-github-url>#your-branch
```

## Tests

The buildpack tests use [Docker](https://www.docker.com/) to simulate
Heroku's Cedar and Cedar-14 containers.

To run the test suite:

```
make test
```

Or to just test in cedar or cedar-14:

```
make test-cedar-10
make test-cedar-14
```

The tests are run via the vendored
[shunit2](http://shunit2.googlecode.com/svn/trunk/source/2.1/doc/shunit2.html)
test framework.
