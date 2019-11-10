=====================
Taking Notes With Vim
=====================

:Author: Velibor Zeli
:Copyright: This tutorial has been placed in the public domain.


.. contents::


Vim is renowned as an ultimate tool for text manipulation. Together with
a markup language like reStructuredText and Markdown and minor
configuration settings it becomes highly effective tool for writing
notes and documentations. See `Why You Should Consider Switching to
Electronic Notebooks`_ if you still haven't.

This project provides an example showing how Vim can be used for making
notes together with a markup language such as reStructuredText_ and
Markdown_. In the same time it is a tutorial that introduces users to
Vim's rich toolbox when it comes to dealing with large number of files
(see tutorial_ directory).

.. _reStructuredText: http://docutils.sourceforge.net/rst.html
.. _Markdown: https://daringfireball.net/projects/markdown/
.. _tutorial: ./tutorial/readme.rst


To Plug or Not to Plug
======================

There are several plugins that provide support for note-taking in Vim
vim-notes_, vimwiki_ and riv.vim_, to name a few. These plugins help
navigate, create notes and generating HTML files which can come in handy
(especially for the beginners in Vim). The main problem, however, with
the mentioned plugins is that they confine users to a set of commands
and potentially hinder from expressing creativity in Vim. Additionally,
they support only certain markup languages, some of which might not be
applicable elsewhere.

On the other hand, commands for jumping into and create new files have
always been an integrated part of Vim. Actually, **multiple-file
manipulation is one of the things where Vim shines the brightest**, just
think about Vim's buffers, argument lists, multiple windows and tabs
options. Also, writing notes in bare Vim does not restrict to a
particular markup language.

.. _vim-notes: https://github.com/xolox/vim-notes
.. _vimwiki: https://github.com/vimwiki/vimwiki
.. _riv.vim: https://github.com/gu-fan/riv.vim


The Vim Way |trademark| of Taking Notes
=======================================

This project builds on top of Vim's capability to work with multiple
files simultaneously. Note-taking requires flexibility and that is
exactly what Vim delivers.

First of all, when working with multiple files configure your
environment so that it support so-called fuzzy search by setting ``set
path+=**`` and ``set wildmenu``. These settings, unfortunately, don't
get the attention they deserve considering that they upgrade Vim from an
airplane to a spaceship. With this configuration, you want to start
building a habit of opening files in Vim from the top-most directory of
a project. This allows using ``:find`` with autocomplete (``TAB``) to
easily jump into files scattered throughout the project. In case there
is a filename in the text simply move the cursor over the name of the
file and press ``gf`` to go to that file. Not to mention that both
``:find`` and ``gf`` are able to open files directly into multiple
windows. If that is not enough try setting ``suffixesadd`` and
``includeexpr`` to open files without typing their file extensions, as
well as by requesting Vim to manipulate file names before opening them.
These two amazing features allow you to use any kind of markup language
you want for writing notes. Would you like to create files while in Vim?
Choose which one works better for you ``:new`` or ``:e``.

It's easy to lose track of opened files but rest assured that the Vim
buffer keeps a list for you, all you need to do is ask ``:ls``. Editing
a file from the buffer is as easy as saying ``:b{pattern}`` where
``{pattern}`` is a unique part in the file name, which could be even a
single letter! This gets even simpler if you want to go back to a file
where you were a second ago, simply use ``CTRL-6``! If you are good at
keeping track of the jumps you made don't forget to use ``CRTL-o`` and
``CRTL-i``, this will bring you home in a blink of an eye (this one is
easy to overuse, so don't be Hulk - don't smash). At this point, it is
easy to spiral down the rabbit hole and into the world of multiple
windows, multiple tabs and folded contents if you feel like...

All of this and yet we are still scratching the surface of Vim's
capabilities when it comes to editing multiple files, which is what
writing notes is all about. I don't want you to get me wrong, using
plugins can be great. However, certain plugins seem to reinvent some of
Vim's irreplaceable capabilities and don't seem to fit as well with
other Vim tools. Although using the mentioned plugins for writing notes
might not be bad per se, it is probably not optimal when considering
the long run where as using The Vim Way |trademark| for multi-file
processing would be more rewarding.

.. |trademark| unicode:: U+2122 .. TRADEMARK SYMBOL


Configuration
-------------

If you are using Vim make sure to configure your ``~/.vimrc``, however
if you are using Neovim make changes in ``~/config/nvim/init.vim``.

1. Set path in Vim to recursively go into subdirectories with

.. code:: vim

  set path+=**

2. Enable autocompletion in the command line by

.. code:: vim

  set wildmenu

This configuration is not so well-known and enables fuzzy search [1]_.
In Neovim this should be the default, make sure by typing ``:set path?``
and ``:set wildmenu?``.

3. Configure ``suffixesadd`` by adding file extension corresponding to
   the markup language of your choice. If you are planning to use both
   reStructuredText and Markdown for taking notes you can add both
   extensions in the form of comma separated list

.. code:: vim

  set suffixesadd+=.rst,.md

4. It is useful to set up ``includeexpr`` (see ``:help includeexpr``).
   Whenever Vim doesn't find a file it invokes ``includeexpr`` and
   substitutes the searched pattern according to the settings provided.
   If your plan is to work with reStructuredText(``.rst`` files) add

.. code:: vim

  set includeexpr=substitute(substitute(substitute(v:fname,'.html','.rst',''),'^_','',''),'_$','','')

otherwise for Markdown (``.md`` files) add

.. code:: vim

  set includeexpr=substitute(v:fname,'.html','.md','')

Use these commands together with ``autocommand`` if you would like to
have one environment for working with ``.rst`` and other for ``.md``
files (see, ``:help autocmd``, ``:help BufNewFile`` and ``:help
BufRead``).


Usage
-----

If Vim is in your fingers and you know the basics of either
reStructuredText or Markdown syntax writing notes should be a walk in
the park (if needed, brush up your `reStructuredText syntax`_ and
`Markdown syntax`_ or learn the syntax in 5 minutes).

.. _`reStructuredText syntax`: https://docutils.readthedocs.io/en/sphinx-docs/ref/rst/restructuredtext.html#quick-syntax-overview
.. _`Markdown syntax`: https://www.markdownguide.org/basic-syntax

Instead of writing one big .rst or .md file with notes, it is better to
split the notes into smaller files and make the files reference each
other. This improves readability of both the source files and the
resulting HTML. To make references between files use hyperlinks.

Here are examples in reStructuredText with good practices that make
movement between files simpler

.. code::

    See here, foo_ is a hyperlink and a jump point to foo.rst.

    .. _foo:: foo.html

and


.. code::

    Also, `foo <foo.html>`_ is a hyperlink and a jump point to foo.rst but with embedded URL.

In case Vim is configured according to Configuration_, placing the Vim
cursor on any of the following in the text ``foo_``, ``_foo``,
``foo.html``, ``foo.rst`` or ``foo`` and pressing ``gf`` opens
``foo.rst`` if it exists (using ``:find`` command with any of the names
has the same effect).

This way of writing hyperlinks introduces jump points that can be used
for moving around files. Keep in mind that if file ``foo.html`` exists
on Vim's path than ``foo.html`` text is no longer a valid jump point
because Vim would jump directly to ``foo.html`` file instead of
``foo.rst``. However, if it doesn't exist than Vim has no file to find
and ``includeexpr`` activates (see Configuration_) making a
substitution so that instead of ``foo.html`` Vim looks for ``foo.rst``.
Therefore, HTML files should be outside of the directory where source
files are located.


Tips
----

Here are tips that could be applied to multi-file processing in general
and extend beyond just this project:

* Keep ``:set path+=**`` and ``:set wildmenu`` activated and start Vim
  from the top-most directory of your project. Use ``:find`` together
  with autocompletion (``TAB``) to open files inside the project.

* Starting Vim with several files creates an argument list (see ``:help
  args``).

* Use ``-o`` and ``-O`` flags when starting Vim to split multiple files
  into windows horizontally and vertically, or ``-p`` to split the files
  into tabs.

* When writing text files in Vim use text wrapping ``:set textwidth=72``
  (set line length according to your style, e.g., Docutils uses 70
  character long lines for .rst files). Use ``gqip`` to wrap a paragraph
  on which the cursor is located or ``gq`` with visually selected text.

* Use ``:!`` to execute shell command from inside Vim (for example,
  compile .rst or .md files into .html with pandoc without leaving Vim
  session).

* Use ``bufdo`` to execute a command on every file in the buffer list
  (see ``:help bufdo``), e.g., ``:bufdo! normal @r`` applies a macro
  saved in register ``r`` to every file in the buffer list.

Why You Should Consider Switching to Electronic Notebooks
=========================================================

As a PhD student I came to realize that the amount of paper usage in
academia is quite high. Partly due to nature of work which revolves
around reading and writing articles and partly due to the habits that
researchers develop until they reach graduate studies where most of
students use notebooks. However, I see a positive trend where many
researchers are reducing paper consumption.

To stop the unnecessary use of paper, I started making e-notes. Although
there are web sites which provide such services (such as Evernote or
Google Keep) I value my privacy too much to give away personal
information freely. In the same time using plain text files for making
notes just doesn't cut it since the readability of ``.txt`` files is
very poor. Therefore, having more readable file formats such as HTML and
PDF would be favorable.

Even though most of people in academia are used to writing LaTeX,
writing ``.tex`` files is an overkill as it is tedious and time
consuming even for the most advanced among users. This is where
flexibility of markup languages like reStructuredText_ and Markdown_
start to dominate over the well-formulated structure of LaTeX. See
`reStructuredText vs. Markdown`_ if you are unsure which markup language
is better for you [2]_.


.. [1] Unfortunately, this is not so well-known feature. It does not have the complete functionality of plugins such as CommandT_ and ctrlp_, but in my opinion it works great.

.. [2] Personally, I chose reStructuredText since it has more features and is, in my honest opinion, more appropriate when it comes to writing technical documentation.

.. _`reStructuredText vs. Markdown`: https://eli.thegreenplace.net/2017/restructuredtext-vs-markdown-for-technical-documentation/
.. _CommandT: https://github.com/wincent/Command-T
.. _ctrlp: https://github.com/ctrlpvim/ctrlp.vim
