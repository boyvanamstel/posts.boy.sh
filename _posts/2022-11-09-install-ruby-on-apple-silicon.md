---
layout: post
title: "Install native arm64 Ruby through rbenv on Apple Silicon"
date: 2022-11-09
tags: [apple-silicon, ruby, tutorial, jekyll]
description: "A step-by-step guide on how to properly install Ruby on Apple Silicon powered computers."
apps: [carbonize]
---
Having recently acquired an Apple Silicon powered MacBook, I noticed the new architecture comes with a few challenges:
1. There are no native binaries available for older applications. This includes legacy versions of Ruby,  Python and other tools.
1. You have to take care to not mix `arm64` and `x86_64`.

These two points combined mean that you might have to upgrade some of your projects. I had to migrate all my websites from Jekyll 3.x on Ruby 2.x to Jekyll 4.3.1 on Ruby 3.1.2.

_Fight the urge to try and get your projects running with outdated software. You'll quickly run into issue number two and be tempted to run your Terminal under Rosetta, like some posts suggest. Please don't do this. You'll regret it later._

In this guide I'll help you install Homebrew, rbenv and a recent version of Ruby all compiled for the `arm64` architecture.

## Setup

Before we get started, make sure you're not already running your Terminal of choice under Rosetta:
1. Right-click your Terminal app.
1. Make sure Open Using Rosetta is disabled.

### Remove `x86_64` installations if necessary

If you've somehow migrated your Homebrew, rbenv or Ruby installations from a previous Intel Mac, you'll first have to uninstall the `x86_64` code.

Just to be sure, check if you have any files present under `/usr/local`. That's was the path Homebrew used before. The new path is `/opt/Homebrew`.

#### rbenv

```bash
brew uninstall rbenv
```

Check if there's anything left under `~/.rbenv`. Get rid of the folder if it's still there.

#### Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh)"
```


## Install Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Make sure the following line is present in your `~/.zshrc` (or other shell's config):
```bash
export PATH="/opt/Homebrew/bin:$PATH"
```

## Install rbenv

```bash
brew install rbenv readline openssl
```

Add the following lines to your `~/.zshrc` (or other shell's config):
```bash
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init -)"
```

## Install Xcode's Command Line Tools

You might already have Xcode and its Command Line Tools installed, but there is a chance that rbenv won't find it.

You can find the standalone release here: [https://developer.apple.com/download/all/](https://developer.apple.com/download/all/).

## Install Ruby

Add the following to your `~/.zshrc` (or other shell's config):
```bash
local READLINE_PATH=$(brew --prefix readline)
local OPENSSL_PATH=$(brew --prefix openssl)

export LDFLAGS="-L$READLINE_PATH/lib -L$OPENSSL_PATH/lib"
export CPPFLAGS="-I$READLINE_PATH/include -I$OPENSSL_PATH/include"
export PKG_CONFIG_PATH="$READLINE_PATH/lib/pkgconfig:$OPENSSL_PATH/lib/pkgconfig"

export RUBY_CONFIGURE_OPTS="--with-openssl-dir=$OPENSSL_PATH"

export PATH=$OPENSSL_PATH/bin:$PATH

export SDKROOT="$(xcrun --show-sdk-path)"
```

This makes sure the compiler knows where to find all the dependencies it requires.

Now get a list of the most recent Ruby versions:
```bash
rbenv install --list
```
Output:
```bash
2.6.10
2.7.6
3.0.4
3.1.2
jruby-9.3.9.0
mruby-3.1.0
picoruby-3.0.0
rbx-5.0
truffleruby-22.3.0
truffleruby+graalvm-22.3.0

Only latest stable releases for each Ruby implementation are shown.
Use 'rbenv install --list-all / -L' to show all local versions.
```

Depending on when you run this command the output will be different. Just pick the latest release.

_If you need Ruby 2, you might have to install OpenSSL 1.1.x. To do this, change every mention of `openssl` to `openssl@1.1`. So, `brew install openssl@1.1` and `local OPENSSL_PATH=$(brew --prefix openssl@1.1)`._

To install Ruby 3.1.2:
```bash
rbenv install 3.1.2
```

Hopefully the command will now complete successfully and you'll be able to use Ruby. To make it the default on your system use this:
```bash
rbenv global 3.1.2
```

**That's it. All done.** 🥳
