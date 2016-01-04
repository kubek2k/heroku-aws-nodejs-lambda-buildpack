# AWS Node.js Lambda deploy heroku buildpack

Shameless modification of https://github.com/kubek2k/heroku-aws-java-lambda-buildpack

## Usage

### Set the buildpack

```
$ heroku buildpacks:set https://github.com/kubek2k/heroku-aws-nodejs-lambda-buildpack
```

### Set env variables

  * `_LAMBDA_FUNCTION_ARN` - the ARN of lambda that is going to be deployed to
  * `_AWS_ACCESS_KEY_ID` - AWS access key id used for deployment
  * `_AWS_SECRET_ACCESS_KEY` - AWS secret key used for deployment
  * `_AWS_DEFAULT_REGION` - AWS region to be used

All env variables starting with `_` sign are not injected into `env.properties` file

**URGENT:** The user owning the AWS access key :point_up: should have permissions to update function code (`Action: ["lambda:UpdateFunctionCode"]`)

### Push the code

```
$ git push heroku master
```

### Deploy code with injected configuration to AWS

```
$ heroku run deploy
```

