[![CircleCI](https://circleci.com/gh/denisshevchenko/breadu.info.svg?style=shield&circle-token=17c278ce24f3329b9d2f8039410020ead3f9ecb2)](https://circleci.com/gh/denisshevchenko/breadu.info)&nbsp;&nbsp;&nbsp;&nbsp;[![Code Climate](https://codeclimate.com/github/codeclimate/codeclimate/badges/gpa.svg)](https://codeclimate.com/github/denisshevchenko/breadu.info)

# Bread Unit

## What is it?

This is a bread unit calculator for diabetics. My son has type 1 diabetes (T1D), so I created this small service for our family as well as for other people who live with this condition.

1 bread unit (BU) corresponds to a quantity of food that contains 10-12 grams of digestible carbohydrates. Calculator converts quantity of particular food from grams to BU and vice versa. You can choose food from the list or just specify carbohydrate value (carb per 100g of food).

Also you can add few products and specify quantity for each of them (i.e. describe your dinner). In this case calculator will get you a total number of BU, it's useful for insulin therapy.

If you have any questions, critique or suggestions for this project - please [email me](mailto:me@dshevchenko.biz).

**Please note that I'm not endocrinologist and this service cannot be treated as an official medical nutrition guide for diabetics.**

### Common Food

Calculator works with a common list of food obtained from the `food/common.csv` file. Carbohydrate values are taken from the public medical resources and from products' labels.

## Real-Life Haskell

Second purpose of this project is a practical programming learning. I use the [Haskell programming language](https://haskell-lang.org/), all modules and configuration files contain a lot of comments to help students understand this small, but real-life Haskell web project. I suppose that you already familiar with Haskell (e.g. you have read [LYAH](http://learnyouahaskell.com/) book or [my book](https://www.ohaskell.guide/)). But don't be afraid!: this project is _designed_ for novices, so basic knowledge of the Haskell and web development is quite enough.

You'll learn such things as:

* structure of the Haskell project and work with [Stack](https://docs.haskellstack.org/en/stable/README/),
* CLI arguments parsing with [optparse-simple](http://hackage.haskell.org/package/optparse-simple),
* work with CSV with [Cassava](https://hackage.haskell.org/package/cassav://hackage.haskell.org/package/cassava),
* type-level web API with [Servant](http://haskell-servant.readthedocs.io/en/stable/),
* front-end generation with [Blaze](https://jaspervdj.be/blaze://jaspervdj.be/blaze/) and [Clay](http://fvisser.nl/clay/).
* documentation with [Haddock](https://www.haskell.org/haddock/),
* CI and CD with [CircleCI](https://circleci.com/),
* automated code review with [Code Climate](https://codeclimate.com/),
* and much more.

Please feel free to [open an issue](https://github.com/denisshevchenko/breadu.info/issues) if you found a bug or want to improve this project.

## Project structure

### Configuration

* `breadu.cabal` - main configuration file.
* `stack.yaml` - configuration file for Stack.
* `circle.yml` - configuration file for CircleCI service.
* `.codeclimate.yml` - configuration file for Code Climate service.

### Source code overview

* `app/` - source code for a program.
    * `CLI.hs` - work with app's command line arguments.
    * `Main.hs` - app's main-function is defined here.

* `lib/` - source code for a library using by a program.
    * `BreadU.hs` - exposed module of the library.
        * `BreadU/API.hs` - web API, defines endpoints.
        * `BreadU/Handlers.hs` - handlers for endpoints.
        * `BreadU/Server.hs` - server that combines API with handlers.
        * `BreadU/Types.hs` - common types.
        * `BreadU/Pages/` - modules for generate pages, in wide sence of word (HTML-markup, CSS, JS and DOM-parts).
        * `BreadU/Tools/` - tools for parsing food, validating user's food data, calculating and suggestions.

* `Setup.hs` - autogenerated module, you haven't touch it.

### Build artifacts

* `.stack-work/` - build artifacts: packages, autogenerated modules, executable file, Haddock-documentation, etc.

### Misc

* `static/` - static web files (actually just images).
* `food/common.csv` - .csv-file with common food (default set of food every user will see).

## Local build

You can build service locally. Assumed that you already have [Haskell Stack](https://docs.haskellstack.org/en/stable/README/). Do:

```
$ git clone git@github.com:denisshevchenko/breadu.info.git
$ cd breadu.info
$ stack setup
$ stack build
```

After that run it:

```
$ stack exec -- breadu-exe -p 3000
```

Then go to [localhost:3000](http://localhost:3000).

That's it. To see short help info do:

```
$ stack exec -- breadu-exe --help
```
