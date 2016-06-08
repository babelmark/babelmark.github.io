---
layout: default
permalink: /faq/
title: faq
---
FAQ
===

[← Back to Babelmark](/)

The original text of this [FAQ from babelmark2](http://johnmacfarlane.net/babelmark2/faq.html) is copyrighted by John Mac Farlane


-   [What is this for?](#what-is-this-for)
-   [What are some examples of interesting divergences between
    implementations?](#what-are-some-examples-of-interesting-divergences-between-implementations)
    -   [Lists](#lists)
    -   [Links](#links)
    -   [Inline markup](#inline-markup)
    -   [Raw HTML](#raw-html)
    -   [Other](#other)
-   [Why does it matter whether implementations
    agree?](#why-does-it-matter-whether-implementations-agree)
-   [What are some big questions that the markdown spec does not
    answer?](#what-are-some-big-questions-that-the-markdown-spec-does-not-answer)
-   [What was the previous Babelmark 1?](#what-was-the-previous-babelmark)
-   [What was Babelmark 2?](#what-was-babelmark-2)
-   [What is Babelmark 3?](#what-is-babelmark-3)
-   [How can I add my markdown implementation to Babelmark
    2?](#how-can-i-add-my-markdown-implementation-to-babelmark-2)
-   [Why is there a 1000 character limit on
    input?](#why-is-there-a-1000-character-limit-on-input)
-   [What determines the order in which the implementations are
    listed?](#what-determines-the-order-in-which-the-implementations-are-listed)

What is this for?
-----------------

This is a tool for comparing the output of various implementations of John Gruber’s [markdown](http://daringfireball.net/projects/markdown/) syntax for plain text documents. The [official markdown syntax documentation](http://daringfireball.net/projects/markdown/syntax) is silent or vague on many issues, and implementations have diverged in their interpretations of the syntax. Even when the interpretation of the syntax spec is not in question, implementations may have bugs. So it is useful to be able to see at a glance how implementations differ on various inputs. The hope is that this tool will promote discussion of how and whether certain vague aspects of the markdown spec should be clarified.

What are some examples of interesting divergences between implementations?
--------------------------------------------------------------------------

### Lists

-   [Sublists and the four space
    rule](/?normalize=1&text=-+top%0A+-+indented+one%0A++-+indented+two%0A+++-+indented+three%0A++++-+indented+four%0A+++++-+indented+five%0A)
-   [Sublist with negative
    indentation](/?normalize=1&text=+-+one%0A-+two%0A%0A)
-   [List continuations and the four space
    rule](/?normalize=1&text=1.+list%0A%0A++continued%0A%0A)
-   [Right-aligned ordered list
    numbers](/?normalize=1&text=+8.+item+1%0A+9.+item+2%0A10.+item+2a)
-   [Consecutive
    lists](/?normalize=1&text=-+foo%0A-+bar%0A%0A1.+first%0A2.+second%0A)
-   [Empty list item](/?normalize=1&text=-+one%0A-%0A-+three%0A)
-   [Lists and
    HRs](/?normalize=1&text=%2B+++item+1%0D%0A%0D%0A++++%2B+++item+2%0D%0A%0D%0A+*+++*+++*+++*+++*)
-   [Heterogeneous
    lists](/?normalize=1&text=1.+a%0A-+x%0A-+y%0A%0A2.+b%0A-+x%0A-+y%0A)
-   [Partially tight
    list](/?normalize=1&text=1.+one%0A%0A2.+two%0A3.+three%0A)
-   [Header in list item](/?normalize=1&text=-+%23+hi%0A%0A)
-   [List items and code
    spans](/?normalize=1&text=-+%60a+long+code+span+can+contain+a+hyphen+characater+like+this%0A++-+and+it+can+screw+things+up%60%0A%0A%0A%0A)

### Links

-   [Spaces in URL](/?normalize=1&text=%5Blink%5D(%2Furl+with+space)%0A)
-   [Link with emphasis including
    bracket](/?normalize=1&text=%5Blink+*with+emph%5D*%5D(%2Furl))
-   [Spaces in reference
    links](/?normalize=1&text=%5Bfoo+bar%5D%5B%5D%0A%0A%5Bfoo++bar%5D%3A+%2Furl%0A%0A%0A%0A%0A%0A%0A%0A%0A%0A)
-   [Escapes in title
    attribute](/?normalize=1&text=%5Bhi%5D(%2Furl+%22with+title%5C)%22)%0A%0A)
-   [Reference link definition in
    blockquote](/?normalize=1&text=%3E+%5Bfoo%5D%5B%5D%0A%3E%0A%3E+%5Bfoo%5D%3A+%2Furl%0A)
-   [Can an inline link contain a space after the square
    bracket?](/?normalize=1&text=%5Bhi%5D+(%2Furl)%0A)
-   [URL with
    parentheses](/?normalize=1&text=%5Bhi%5D(%2Furl(with+parens))%0A)
-   [Link with
    backticks](/?normalize=1&text=%5Bthis+%60is+a%5D+link%60+with+backticks%5D(%2Furl)%0A)
-   [Case-insensitive reference links with
    unicode](/?normalize=1&text=%5B%D0%A2%D0%BE%D0%BB%D0%BF%D0%BE%D0%B9%5D+is+a+Russian+word.%0A%0A%5B%D0%A2%D0%9E%D0%9B%D0%9F%D0%9E%D0%99%5D%3A+%2Furl%0A)
-   [Unicode and tab
    conversion](/?normalize=1&text=%60%D0%A2%D0%BE%09%D0%BB%D0%BF%D0%BE%D0%B9%60+is+a+Russian+word+with+a+tab+inside.%0A)
-   [Disappearing reference
    links!](/?normalize=1&text=%5BLike+this%5D%5Bd%5D%3A+%5Bhere%5D%5Bh%5D.%0A%0A%5Bd%5D%3A+foo%0A%5Bh%5D%3A+ba)
-   [Entities in
    autolinks](/?normalize=1&text=%3Chttp%3A%2F%2Fg%26ouml%3B%26ouml%3Bgle.com%3E%0A%0A)
-   [Entities in
    URLs](/?normalize=1&text=%5Blink%5D(http%3A%2F%2Fg%26ouml%3B%26ouml%3Bgle.com)%0A%0A%0A)
-   [Links inside
    links](/?normalize=1&text=%5Blink+%5Bin+link%5D(%2Furl)%5D(%2Furl2)%0A)
-   [Escaped
    image](/?normalize=1&text=%5C!%5Bnot+an+image%5D(%2Furl.jpg)%0A)
-   [Unmatched
    backticks](/?normalize=1&text=hello+%60%60%60there%60%60.%0A)
-   [What to do when a reference link is
    undefined?](/?normalize=1&text=%5Bfoo%5D%3A+%2Fbar%0A%0A%5Bfoo%5D%5B1%5D)
-   [Reference link
    precedence](/?normalize=1&text=%5Bfoo%5D%5Bbar%5D%5Bbaz%5D%0A%0A%5Bbaz%5D%3A+%2Furl%0A)
-   [Reference link
    indentation](/?normalize=1&text=%5Blink+test%5D%5B0%5D%0A%5Blink+test%5D%5B1%5D%0A%5Blink+test%5D%5B2%5D%0A%5Blink+test%5D%5B3%5D%0A%5Blink+test%5D%5B4%5D%0A%0A%5B0%5D%3A%5Bhttp%3A%2F%2Fexample.com%5D%0A+%5B1%5D%3A%5Bhttp%3A%2F%2Fexample.com%5D%0A++%5B2%5D%3A%5Bhttp%3A%2F%2Fexample.com%5D%0A+++%5B3%5D%3A%5Bhttp%3A%2F%2Fexample.com%5D%0A++++%5B4%5D%3A%5Bhttp%3A%2F%2Fexample.com%5D%0A)

### Inline markup

-   [Nested emph and
    strong](/?normalize=1&text=***bold**+in+ital*%0A%0A***ital*+in+bold**)
-   [Precedence, emphasis and code
    span](/?normalize=1&text=*hi+%60there*%60%0A)
-   [Emphasis precedence](/?normalize=1&text=*hi***there*%0A)
-   [Emphasis nesting](/?normalize=1&text=*a+**b+*a+**b**+a*+b**+a*%0A)
-   [Backticks in code
    span](/?normalize=1&text=%60+%60%60code%60%60+%60%0A)
-   [Escaped asterisk](/?normalize=1&text=*hi%5C*+there*%0A)

### Raw HTML

-   [Capitalized DIV
    tags](/?normalize=1&text=%3CDIV%3E%0Ahi%0A%3C%2FDIV%3E%0A)
-   [`<ins>` tag around
    paragraph](/?normalize=1&text=%3Cins%3EInserted+paragraph.%3C%2Fins%3E%0A%0A)
-   [Commented out list
    item](/?normalize=1&text=-+one%0A%3C!--%0A+-+two+%0A--%3E%0A-+three%0A)
-   [Commented out reference link
    definition](/?normalize=1&text=%5Bfoo%5D%0A%0A%3C!--%0A%0A%5Bfoo%5D%3A+%2Furl%0A%0A--%3E%0A)

### Other

-   [Collapsing
    blockquotes](/?normalize=1&text=%3E+one%0A%0A%3E+two%0A%0A%3E+three%0A%3E%0A%3E+four%0A)
-   [Unescaped
    `<`](/?normalize=1&text=x%3Cmax%3Ccode%3Ea%2Cb%3C/code%3E%0D%0A)
-   [Newline after code block?](/?normalize=1&text=++++code%0A)
-   [Are two spaces at end of paragraph a
    linebreak?](/?normalize=1&text=hi++)
-   [Unknown
    entities](/?normalize=1&text=under+a+lciense+from+AT%26T%3B+however%2C%0A)
-   [Markup in image alt
    tag](/?normalize=1&text=!%5B*%5Balt%5D(%2Furl)*%5D(img.jpg)%0A)
-   [Blank line needed before code
    block?](/?normalize=1&text=hi%0A++++there%0A)
-   [Dash patterns](/?normalize=1&text=-%0A--%0A---%0A--%0A-%0A)
-   [ATX headers with
    escapes](/?normalize=1&text=%23%23+hi%5C%23%23%23%0A)
-   [Setext header? with two spaces at
    end](/?normalize=1&text=hello++%0A-----%0A%0A%0A)
-   [Inlines in
    headers](/?normalize=1&text=%23+Hello+%5Bthere%0A+++people%5D(%2Furl)%0A)

Why does it matter whether implementations agree?
-------------------------------------------------

Markdown is everywhere these days. If the same document is interpreted differently in different places, that is a problem. For example, suppose you have a nice piece of documentation on a github wiki, and you want to turn it into DocBook using pandoc. Your sublists are indented two spaces, and this works fine on the wiki, but when you run the document through pandoc, these items are interpreted as parts of the main list. If you are lucky, you notice this before distributing the DocBook file!

What are some big questions that the markdown spec does not answer?
-------------------------------------------------------------------

1.  How much indentation is needed for a sublist? The spec says that
    continuation paragraphs need to be indented four spaces, but is not
    fully explicit about sublists. It is natural to think that they,
    too, must be indented four spaces, but [not all implementations
    require
    that](/?normalize=1&text=-+top%0A+-+indented+one%0A++-+indented+two%0A+++-+indented+three%0A++++-+indented+four%0A%0A%0A%0A).
    (Note that none of the implementations that allow a one-space
    indentation to start a sublist are entirely consistent about that.)
    This is hardly a “corner case,” and divergences between
    implementations on this issue often lead to surprises for users in
    real documents. See [this comment by John
    Gruber](http://article.gmane.org/gmane.text.markdown.general/1997).

2.  Is a blank line needed before a block quote or header? Or can you
    have things [like
    this](/?normalize=1&text=paragraph%0A%3E+block+quote%0A%23+header%0Aparagraph%0A):

        paragraph
        > block quote
        # header
        paragraph

    Most implementations do not require the blank line. However, this
    can lead to unexpected results in hard-wrapped text, and also to
    ambiguities in parsing (note that some implementations put the
    header inside the blockquote, while others do not). John Gruber has
    also spoken [in favor of requiring the blank
    lines](http://article.gmane.org/gmane.text.markdown.general/2146).

3.  Is blank space allowed between the `[...]` part and the `(...)` part
    of an inline link? That is, can you have a link [like
    this](/?normalize=1&text=%5Bmy+link%5D+(%2Furl)):

        [my link] (/url)

    There is [some relevant discussion
    here](http://article.gmane.org/gmane.text.markdown.general/4513).

4.  What is the exact rule for determining when list items get wrapped
    in `<p>` tags? Can a list be partially loose and partially tight?
    What should we do with [a list like
    this](/?normalize=1&text=1.+one%0A%0A2.+two%0A3.+three%0A):

        1. one

        2. two
        3. three

    Or
    [this](/?normalize=1&text=1.++one%0A%0A++++-+a%0A%0A++++-+b%0A2.++two%0A)?

        1.  one

            - a

            - b
        2.  two

    There are some relevant comments by John Gruber
    [here](http://article.gmane.org/gmane.text.markdown.general/2554).

5.  When list markers change from bullets to numbers, should we have
    [two lists or
    one](/?normalize=1&text=-+foo%0A-+bar%0A%0A1.+foo%0A2.+bar%0A)?

6.  Should two blockquotes with a blank line between them be treated [as
    a single blockquote](/?normalize=1&text=%3E+one%0A%0A%3E+two%0A%0A)?
    Most implementations do this, but John Gruber has suggested [that
    this be
    changed](http://article.gmane.org/gmane.text.markdown.general/2206).
    (Waylan Limberg [points
    out](http://www.mail-archive.com/markdown-discuss@six.pairlist.net/msg02750.html)
    that the spec actually does seem to settle this question, in favor
    of a single blockquote.)

7.  Can reference link definitions occur [embedded in block quotes and
    list
    items](/?normalize=1&text=1.++%5Bfoo%5D%5B%5D%0A%0A++++%5Bfoo%5D%3A+%2Ffoo%0A%0A%3E+%5Bbar%5D%5B%5D%0A%3E%0A%3E+%5Bbar%5D%3A+%2Fbar%0A)?
    (The spec says they can be “anywhere in the document,” but most
    implementations require that they be at the outer level.)

What was the previous Babelmark?
---------------------

The original Babelmark at <http://babelmark.bobtfish.net> was written by Michel Fortin, author of PHP Markdown and PHP Markdown Extra. It is no longer accessible. It was using old implementations.

What was Babelmark 2?
---------------------

John Mac Farlane introduced a new version called [babelmark2](http://johnmacfarlane.net/babelmark2). 

Instead of asking the Babelmark maintainer to install all the converters on his server, and keep them up to date, we use a decentralized model. Each implementer provides a small “dingus server” that accepts textual input and returns HTML. Babelmark 2 queries these dingus servers asynchronously and combines their outputs into a page of results. This system puts the burden on implementers to keep their servers up to date.


What is Babelmark 3?
---------------------------------------------

This new version was developed by Alexandre Mutel and is using the same concept as Babelmark 2, by acting as a proxy to other markdown convert servers. The differences are:

- the project [babelmark](https://github.com/babelmark) is now hosted on github, accepting PR
- the front-end (this site) is hosted on github-pages, the repository is [babelmark.github.io](https://github.com/babelmark/babelmark.github.io) using a plain jekyll website.
  - Relooking  
  - Use of ajax query instead of post form
- the back-end [babelmark-proxy](https://github.com/babelmark/babelmark-proxy) is hosted on Azure and is a .NET application.
  - Multithreads queries to markdown convert servers
  - Perform normalization on the server
- the [babelmark registry](https://github.com/babelmark/babelmark-registry) contains the list of markdown convert servers

How can I add my markdown implementation to Babelmark 2?
--------------------------------------------------------

Write a server app or CGI script that accepts accepts GET queries, takes the text out of the `text` parameter, and returns a javascript object with the following fields: `name` (the name of the markdown processor), `version` (the version being run), and `html` (the result of converting
the text to HTML).

Example:

    $ curl 'http://johnmacfarlane.net/cgi-bin/pandoc-dingus?text=hi'
    {"name":"Pandoc","html":"<p>hi</p>","version":"1.9.4.2"}

The script can, if desired, return an error if the input text exceeds 1000 characters.

The fork the repository [babelmark registry](https://github.com/babelmark/babelmark-registry) and add your server to the file `registry.json`

Why is there a 1000 character limit on input?
---------------------------------------------

A thousand characters should be sufficient to test syntax features. We impose the limit to reduce load on the servers.

What determines the order in which the implementations are listed?
------------------------------------------------------------------

The calls to the individual dingus servers are made asynchronously and in different threads, the results added in the order they come in. However, one should not infer that the implementations that appear at the top are the fastest.
The performance differences in converting small bits of markdown are swamped by other factors, such as server latency and script startup time. For example, RedCarpet has the fastest parser of all the
implementations, but often appears last because of the slow startup time of ruby scripts. And PHP Markdown is faster than Markdown.pl, but its dingus server is much farther away.
