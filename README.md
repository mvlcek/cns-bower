# Bower

[![Build Status](https://travis-ci.org/bower/bower.svg?branch=master)](https://travis-ci.org/bower/bower) [![Coverage Status](https://coveralls.io/repos/bower/bower/badge.png?branch=master)](https://coveralls.io/r/bower/bower?branch=master)

<img align="right" height="300" src="http://bower.io/img/bower-logo.png">

> A package manager for the web

**This is a fork, which extends bower by a maven resolver**

Bower offers a generic, unopinionated solution to the problem of **front-end package management**, while exposing the package dependency model via an API that can be consumed by a more opinionated build stack. There are no system wide dependencies, no dependencies are shared between different apps, and the dependency tree is flat.

Bower runs over Git, and is package-agnostic. A packaged component can be made up of any type of asset, and use any type of transport (e.g., AMD, CommonJS, etc.).

**View complete docs on [bower.io](http://bower.io)**

[View all packages available through Bower's registry](http://bower.io/search/).

## Install

```sh
$ npm install -g bower
```

Bower depends on [Node.js](http://nodejs.org/) and [npm](http://npmjs.org/). Also make sure that [git](http://git-scm.com/) is installed as some bower
packages require it to be fetched and installed.


## Usage

See complete command line reference at [bower.io/docs/api/](http://bower.io/docs/api/)

### Installing packages and dependencies

```sh
# install dependencies listed in bower.json
$ bower install

# install a package and add it to bower.json
$ bower install <package> --save

# install specific version of a package and add it to bower.json
$ bower install <package>#<version> --save
```

### Using packages

We discourage using bower components statically for performance and security reasons (if component has an `upload.php` file that is not ignored, that can be easily exploited to do malicious stuff).

The best approach is to process components installed by bower with build tool (like [Grunt](http://gruntjs.com/) or [gulp](http://gulpjs.com/)), and serve them concatenated or using module loader (like [RequireJS](http://requirejs.org/)).

**Maven extension**: package URLs can use maven+http://... or maven+https://... to access a maven repository (URL up to the package name, not including the version number)

### Uninstalling packages

To uninstall a locally installed package:

```sh
$ bower uninstall <package-name>
```

### prezto and oh-my-zsh users

On `prezto` or `oh-my-zsh`, do not forget to `alias bower='noglob bower'` or `bower install jquery\#1.9.1`

### Extended usage with Maven support

Use case: you have a (private) maven repository (like [artifactory](http://www.jfrog.com/artifactory)), where you deploy bower packages to with a maven build (e.g. by [Jenkins](http://jenkins-ci.org/)).

Install [private bower](http://hacklone.github.io/private-bower/) on one of your servers.

Use this fork of bower on your development machines/continuous build servers:
```sh
$ npm install -g cns-bower
```

Point your bower to the private bower registry by creating a file .bowerrc in your user directory (replace your server name):
```json
{
    "registry": "http://private.bower.server:5678/"
}
```

After the first successful deployment of a bower package to your maven repository, register the package on your private bower registry:
```sh
$ bower register <package> maven+http://your.maven.repository//.../<package>
```

If you use grunt, there is a patched [fork](https://github.com/mvlcek/grunt-bower-task) of [grunt-bower-task](https://github.com/yatskevich/grunt-bower-task), which uses cns-bower:
```sh
$ npm install grunt-cns-bower-task
```

### Running commands with sudo

Bower is a user command, there is no need to execute it with superuser permissions.
However, if you still want to run commands with sudo, use `--allow-root` option.

### Windows users

To use Bower on Windows, you must install
[msysgit](http://msysgit.github.io/) correctly. Be sure to check the
option shown below:

![msysgit](http://f.cl.ly/items/2V2O3i1p3R2F1r2v0a12/mysgit.png)

Note that if you use TortoiseGit and if Bower keeps asking for your SSH
password, you should add the following environment variable: `GIT_SSH -
C:\Program Files\TortoiseGit\bin\TortoisePlink.exe`. Adjust the `TortoisePlink`
path if needed.

## Configuration

Bower can be configured using JSON in a `.bowerrc` file. Read over available options at [bower.io/docs/config](http://bower.io/docs/config).

## Completion (experimental)

_NOTE_: Completion is still not implemented for the 1.0.0 release

Bower now has an experimental `completion` command that is based on, and works
similarly to the [npm completion](https://npmjs.org/doc/completion.html). It is
not available for Windows users.

This command will output a Bash / ZSH script to put into your `~/.bashrc`,
`~/.bash_profile`, or `~/.zshrc` file.

```sh
$ bower completion >> ~/.bash_profile
```


## Support

* [StackOverflow](http://stackoverflow.com/questions/tagged/bower)
* [Mailinglist](http://groups.google.com/group/twitter-bower) - twitter-bower@googlegroups.com
* [\#bower](http://webchat.freenode.net/?channels=bower) on Freenode


## Contributing

We welcome contributions of all kinds from anyone. Please take a moment to
review the [guidelines for contributing](CONTRIBUTING.md).

* [Bug reports](CONTRIBUTING.md#bugs)
* [Feature requests](CONTRIBUTING.md#features)
* [Pull requests](CONTRIBUTING.md#pull-requests)


## Bower Team

Bower is made by lots of people across the globe, contributions large and small. Our thanks to everyone who has played a part.

### Core team

* [@satazor](https://github.com/satazor)
* [@wibblymat](https://github.com/wibblymat)
* [@paulirish](https://github.com/paulirish)
* [@benschwarz](https://github.com/benschwarz)
* [@sindresorhus](https://github.com/sindresorhus)
* [@svnlto](https://github.com/svnlto)
* [@sheerun](https://github.com/sheerun)

### Bower Alumni

* [@fat](https://github.com/fat)
* [@maccman](https://github.com/maccman)


## License

Copyright (c) 2014 Twitter and other contributors

Licensed under the MIT License
