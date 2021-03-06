mincss
======

.. image:: https://travis-ci.org/myint/mincss.png?branch=master
    :target: https://travis-ci.org/myint/mincss
    :alt: Build status

Clears the junk out of your CSS by finding out which selectors are
actually not used in your HTML.

This is an unofficial fork (of https://pypi.python.org/pypi/mincss) that runs
on both Python 2 and 3.

Example
-------

To output to a directory called ``cleaned``::

    $ mincss --output=./cleaned https://github.com


Installation
------------

From pip::

    $ pip install --upgrade mincss3k

Why?
----

With the onslaught of Twitter Bootstrap upon the world it's very
tempting to just download their whole fat CSS and serve it up even
though you're not using half of the HTML that it styles.

There's also the case of websites that have changed over time but
without the CSS getting the same amount of love refactoring. Then it's
very likely that you get CSS selectors that you're no longer or never
using.

This tool can help you get started reducing all those selectors that
you're not using.

Whitespace compression?
-----------------------

No, that's a separate concern. This tool works independent of whitespace
compression/optimization.

For example, if you have a build step or a runtime step that converts
all your CSS files into one (concatenation) and trims away all the
excess whitespace (compression) then the output CSS can still contain
selectors that are never actually used.

What about AJAX?
----------------

If you have a script that creates DOM elements in some sort of
``window.onload`` event then ``mincss`` will not be able to know this
because at the moment ``mincss`` is entirely static.

So what is a web developer to do? Simple, use ``/* no mincss */`` like
this for example:

::

    .logged-in-info {
        /* no mincss */
        color: pink;
    }

That tells ``mincss`` to ignore the whole block and all its selectors.
