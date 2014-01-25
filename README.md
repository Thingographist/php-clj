# php-clj [![Build Status](https://travis-ci.org/mudge/php-clj.png?branch=master)](https://travis-ci.org/mudge/php-clj)

A Clojure library to deserialize PHP as generated by
[`serialize`](http://php.net/manual/en/function.serialize.php) into Clojure
data structures and vice versa.

## Usage

```clojure
(ns foo.bar
  (:require [php_clj.core :refer [php->clj clj->php]]))

(php->clj "s:18:\"Café Scientifique\";")
;; => "Café Scientifique"

(php->clj "i:1337;")
;; => 1337

(php->clj "a:2:{s:4:\"Wöo\";a:3:{i:0;i:1;i:1;i:2;i:2;i:3;}s:3:\"Bar\";b:0;}")
;; => {"Bar" false, "Wöo" {2 3, 1 2, 0 1}}

(clj->php "Café")
;; => "s:5:\"Café\";"
```

## A Note on PHP Arrays

As [PHP's Arrays](http://www.php.net/manual/en/language.types.array.php) are
actually maps, converting an array such as `array(1, 2, 3)` will result in a
Clojure map `{0 1, 1 2, 2 3}`.

## Installation

php-clj is available on [Clojars](https://clojars.org/php-clj), add the
following to your [Leiningen](https://github.com/technomancy/leiningen)
dependencies:

```clojure
[php-clj "0.1.0"]
```

## References

* [Arto Bendiken's `php-s11n`](http://wiki.call-cc.org/eggref/4/php-s11n);
* [Brad Koch's Stack Overflow discussion "Parsing serialized PHP data with BNF
  using
  Instaparse"](http://stackoverflow.com/questions/18518499/parsing-serialized-php-data-with-bnf-using-instaparse).

