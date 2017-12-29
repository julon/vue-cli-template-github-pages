# {{ name }}

> {{ description }}

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
{{#unit}}

# run unit tests
npm run unit
{{/unit}}
{{#e2e}}

# run e2e tests
npm run e2e
{{/e2e}}
{{#if_or unit e2e}}

# run all tests
npm test
{{/if_or}}
```

## Github Pages Setup
Commit the project initial files to the master branch since it is needed for build and deployment by travisCI. Add the remote origin if needed.
``` bash
# commit initial files
git add -A && git commit -m "Initial template files"

# push it to the origin
git push origin master
```
Setup an empty 'gh-pages' branch
``` bash
# checkout an empty orphan branch and unselect staged files
git checkout --orphan gh-pages
git rm --cached -r .

# create an empty commit
git commit --allow-empty -m "initial commit"

# push it to the origin
git push -u origin gh-pages
```

In your new project settings at https://github.com/[username]/[repository-name]/settings, go to the 'Github Pages' section and select gh-pages branch as the source.

Add a custom domain if needed.

Generate a new token at the [Personal Access Token Page](https://github.com/settings/tokens) with 'public_repo' rights or 'repos' if the repository is private.

## TravisCI Setup

Login to travisCI with your Github credentials.

Activate travisCI for your github repository https://travis-ci.org/profile/[username].

Open the settings page on travis : https://travis-ci.org/[username]/[repository-name]/settings.

Add an environment variable named GITHUB_TOKEN and set the value to the token generated previously on the github personal access token page.

After every successful(unit & e2e) commit on branch master, the resulting dist will be deployed. Push a commit on the master branch and make sure it deploys successfully in travisCI build logs.
Browse the url from github pages settings, you should see the vuejs webpack basic template.

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
