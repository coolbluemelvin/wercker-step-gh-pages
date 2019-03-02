# wercker-step-gh-pages

Deploy to Github Pages with Wercker.

## Usage

Put __coolbluemelvin/gh-pages__ step into your wercker.yml.

Please make sure your wercker-box contains 'git' command.

### Example(Docker-stack)

```yaml
box: golang:1.5.1
build:
  steps:
    - arjen/hugo-build:
        basedir: "/"
        version: "0.53"
        theme: hello-friend-ng
        flags: --buildDrafts=true
deploy:
  steps:
    - coolbluemelvin/gh-pages:
        token: $GITHUB_TOKEN
        repo: randompaper/randompaper.github.io
        path: public
        domain: randompaper.co
```

Then set your Github [Personal Access Token](https://github.com/settings/tokens)  as environment variables.

![Deployment variables](http://randompaper.co.s3.amazonaws.com/github.com/coolbluemelvin/wercker-step-gh-pages/deploy-variables.png)

Finally, you will be able to deploy to Github Pages.

## Options

|name|description|optional|
|----|-----------|--------|
|token|Github token|false|
|repo|Destination repository|true/false|
|domain|Custom domain|true|
|path|Root dir|true|
