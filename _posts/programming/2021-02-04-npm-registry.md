---
layout: post
title:  "npm registry from github"
date:   2021-02-04 20:00:00
categories: programming
---

**UPDATE**

Don't do this. Github Actions Token does not have the privilege to publish the npm package.
You always need a personal access token with full repo access. This sucks!

## Authentication

create a **personal access token** with packages write or read privilege

then in your home directory create a file .npmrc` with the content:

```
//npm.pkg.github.com/:_authToken=8474474893739004394040xxxxxxxxxxxxxxxxxx
```

## Publish a Package

in your `package.json` put a scope to the name: `@owner/name`

in the same dir create a file named `.npmrc` with the content:

```
registry=https://npm.pkg.github.com/OWNER
```

commit and push the file

in the `package.json` there must be a `repository` field with the content: `git://github.com/OWNER/REPO.git`

then publish the package:

```
npm publish
```


## Install a Package

in the client project create a file `.npmrc` with the content:

```
registry=https://npm.pkg.github.com/OWNER
```

then add the scoped dependency to `package.json` like `@owner/libname`

then run:

```
npm install
```