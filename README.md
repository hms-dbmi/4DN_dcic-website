### 4DN DCIC Website

The 4DN DCIC website is built with [Jekyll](http://jekyllrb.com), [SASS](http://www.sass-lang.com), [Bourbon](http://bourbon.io), [Neat](http://neat.bourbon.io), and [Bitters](http://bitters.bourbon.io).

#### Prerequisites

A Ruby installation is required to work with Jekyll.

#### Setup

Requires Jekyll 3.0.0 and the Github Pages configuration.

```ShellSession
$ gem install github-pages
```

#### Generate and/or Serve Site

```ShellSession
$ jekyll serve --watch
```

#### View Site

```ShellSession
$ open http://127.0.0.1:4000/
```

### Updating Bourbon Dependencies

__This should not be necessary under normal circumstances!__ To update the dependencies on Bourbon, Neat or Bitters additional gems are required.

```ShellSession
$ gem install bourbon
$ gem install neat
$ gem install bitters
```
Depending on your system your might have to run those as superuser using ```sudo```.

### Github Pages

https://help.github.com/categories/github-pages-basics/

### Jekyll Website

http://jekyllrb.com

### Liquid Syntax

https://github.com/Shopify/liquid/wiki/Liquid-for-Designers

