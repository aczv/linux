---
title: Nanoc.ws
---

## Links

* [Install Ruby on Rails][installruby]

[installruby]: https://www.digitalocean.com/community/tutorials/how-to-install-ruby-on-rails-with-rbenv-on-ubuntu-14-04

Follow step-by-step instructions on Digital Ocean to install Ruby.

## Install rbenv

First, update apt-get:

    sudo apt-get update

Install the rbenv and Ruby dependencies with apt-get:

    sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev

Now we are ready to install rbenv. The easiest way to do that is to run these commands, as the user that will be using Ruby:

    cd
    git clone git://github.com/sstephenson/rbenv.git .rbenv
    echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
    echo 'eval "$(rbenv init -)"' >> ~/.bashrc
    
    git clone git://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
    echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
    source ~/.bashrc

## Install Ruby

As the user that will be using Ruby, install it with these commands:

    rbenv install -v 2.2.1
    rbenv global 2.2.1

The global sub-command sets the default version of Ruby that all of your shells will use. If you want to install and use a different version, simply run the rbenv commands with a different version number.

Verify that Ruby was installed properly with this command:

    ruby -v

It is likely that you will not want Rubygems to generate local documentation for each gem that you install, as this process can be lengthy. To disable this, run this command:

    echo "gem: --no-document" > ~/.gemrc

You will also want to install the bundler gem, to manage your application dependencies:

    gem install bundler

## Install Rails

As the same user, install Rails with this command (you may specify a specific version with the -v option):

    gem install rails

Whenever you install a new version of Ruby or a gem that provides commands, you should run the rehash sub-command. This will install shims for all Ruby executables known to rbenv, which will allow you to use the executables:

    rbenv rehash

Verify that Rails has been installed properly by printing its version, with this command:

    rails -v

If it installed properly, you will see the version of Rails that was installed.

## Installing Nanoc

All dependencies are now taken care of, and installing Nanoc should now be easy:

    gem install nanoc

To make sure that Nanoc was installed correctly, run nanoc --version. It should print the version number along with some other information, like this:

    nanoc --version

Nanoc 4.0.0 © 2007-2015 Denis Defreyne.
Running ruby 2.2.3 (2015-08-18) on x86_64-darwin14 with RubyGems 2.4.7.

### Set UTF-8 encoding (compile fails on Windows)

Encoding::CompatibilityError: incompatible encoding regexp match (UTF-8 regexp with IBM775 string)

Set environment variable:

	set RUBYOPT=-E utf-8

