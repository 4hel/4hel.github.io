---
layout: post
title:  "TiddlyWiki"
date:   2020-09-17 06:10:00
categories: software
---

[TiddlyWiki](https://tiddlywiki.com/) is an incredibly flexible and versatile tool that is conceived and constructed differently than most software. This can make it hard to understand until the moment when it clicks, and becomes a seamless extension of your brain.

## Installation

```
npm install -g tiddlywiki
tiddlywiki --version

tiddlywiki mynewwiki --init server
tiddlywiki mynewwiki --liste

```

## Export for offline

Use gui to download index.htlm or:

```
tiddlywiki mynewwiki --build index
```

## Import from offline

```
tiddlywiki mynewwiki --import ~/Downloads/index.html text/html
```


## Serverless

Probably node.js in Lambda with **EFS** mounted

## Plugins

AWS plugin is not suitable for hosting lambda, but installation is:

```
git clone https://github.com/Jermolene/TiddlyWiki5.git
mkdir mynewwiki/plugins
cp -rv TiddlyWiki5/plugins/tiddlywiki/aws mynewwiki/plugins/
cp -rv TiddlyWiki5/plugins/tiddlywiki/async mynewwiki/plugins/
cp -rv TiddlyWiki5/plugins/tiddlywiki/jszip mynewwiki/plugins/

tiddlywiki mynewwiki --rendertiddler $:/plugins/tiddlywiki/aws/lambdas/main index.js text/plain
```





