Discount Markdown Processor for Ruby
====================================

This is a very slightly patched version of the official [RDiscount](http://github.com/rtomayko/rdiscount/) 1.6.8.

The patches include:

- enable DIV_QUOTE support, so now you can use markdown inside a classed blockquote or div with the following syntax:

    > %special%
    > ###as you see,
    > - markdown works nicely inside this special div

  This produces the following markup:

    <div class="special"><h3>as you see,</h3> 
      <ul> 
      <li>markdown works nicely inside this special div</li> 
      </ul> 
    </div>

  Instead of class you can also use an ID, using this syntax:

    > %id:special%

- another patch is added so that it compiles nicely (prevents the ['no int of size 4' error](https://github.com/rtomayko/rdiscount/issues/48))


ORIGINAL README
---------------

Discount is an implementation of John Gruber's Markdown markup language in C. It
implements all of the language described in [the markdown syntax document][1] and
passes the [Markdown 1.0 test suite][2].

CODE: `git clone git://github.com/rtomayko/rdiscount.git`  
HOME: <http://github.com/rtomayko/rdiscount>  
DOCS: <http://rdoc.info/projects/rtomayko/rdiscount>  
BUGS: <http://github.com/rtomayko/rdiscount/issues>

Discount was developed by [David Loren Parsons][3]. The Ruby extension
is maintained by [Ryan Tomayko][4].

[1]: http://daringfireball.net/projects/markdown/syntax
[2]: http://daringfireball.net/projects/downloads/MarkdownTest_1.0.zip
[3]: http://www.pell.portland.or.us/~orc
[4]: http://tomayko.com/about

INSTALL, HACKING
----------------

New releases of RDiscount are published to [gemcutter][]:

    $ [sudo] gem install rdiscount -s http://gemcutter.org

The RDiscount sources are available via Git:

    $ git clone git://github.com/rtomayko/rdiscount.git
    $ cd rdiscount
    $ rake --tasks

See the file [BUILDING][] for hacking instructions.

[gemcutter]: http://gemcutter.org/gems/rdiscount
[BUILDING]: BUILDING

USAGE
-----

RDiscount implements the basic protocol popularized by RedCloth and adopted
by BlueCloth:

    require 'rdiscount'
    markdown = RDiscount.new("Hello World!")
    puts markdown.to_html

Additional processing options can be turned on when creating the
RDiscount object:

    markdown = RDiscount.new("Hello World!", :smart, :filter_html)

Inject RDiscount into your BlueCloth-using code by replacing your bluecloth
require statements with the following:

    begin
      require 'rdiscount'
      BlueCloth = RDiscount
    rescue LoadError
      require 'bluecloth'
    end

COPYING
-------

Discount is free software;  it is released under a BSD-style license
that allows you to do as you wish with it as long as you don't attempt
to claim it as your own work. RDiscount adopts Discount's license
verbatim. See the file `COPYING` for more information.

