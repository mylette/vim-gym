==============================
Notes in Vim + Markup Language
==============================

:Author: Velibor Zeli
:Copyright: This tutorial has been placed in the public domain.


.. contents::


Vim is an amazing tool for text manipulation and together with a markup
language like reStructuredText and Markdown, and some minor
configuration settings, it becomes highly effective tool for writing
notes and documentations.

This project has a double purpose. It provides an example how Vim can be
used for making notes together with a markup language. In the same time
it is a tutorial that introduces users to Vim's rich toolbox when it
comes to dealing with large number of files.


To Plug or Not to Plug
======================

There are several plugins that help with note-taking vim-notes_,
vimwiki_ and riv.vim_, just to name a few. These plugins help users
navigate, create notes and even generating HTML files. This extra
functionality in Vim can be helpful (especially for the beginners). The
main problem, however, with these plugins is that they confine users to
a set of commands and potentially hinder from expressing creativity in
Vim. Additionally, they limit users to specific number of markup
languages, some of which might not be applicable elsewhere.

On the other hand, commands for jumping into and create new files have
always been an integrated part of Vim. Actually, multiple-file
manipulation is one of the thing where Vim shines the brightest, just
think about Vim's buffers and argument lists. Also, writing notes in
bare Vim does not restrict users to a particular markup language.

.. _vim-notes: https://github.com/xolox/vim-notes
.. _vimwiki: https://github.com/vimwiki/vimwiki
.. _riv.vim: https://github.com/gu-fan/riv.vim


The Vim Style of Taking Notes
=============================

The workflow in this project is builds on top of Vim's capability to
work with multiple files simultaneously. Note-taking requires
flexibility and that is exactly what Vim delivers.

First of all, when working with multiple files configure your
environment so that it support so-called fuzzy search by setting ``set
path+=**`` and ``set wildmenu``. Unfortunately, these commands are not
appreciated sufficiently, considering that they upgrade Vim from an
airplane to a spaceship. With this configuration, you want to start
building a habit of opening your files in Vim from the top-most
directory of your projects. This allows you to use ``:find`` to easily
jump into files scattered throughout your project using auto-complete.
In case you have a list with items that are names of other files (notes)
simply move the cursor over the name of a file and press ``gf`` to go to
that file. Not to mention that both of these commands are able to open
files directly into multiple windows.  If that is not enough try setting
add ``suffixesadd`` and ``includeexpr`` to open files without typing
their file extensions, as well as by requesting Vim to manipulate file
names before opening them. These two amazing features allow you to use
any kind of markup language you want to write your notes. Would you like
to create files? Chose which works better for you ``:new`` or ``:e``.

It's easy to lose track of opened files but rest assured that the Vim
buffer keeps a list for you, all you need to do is ask ``:ls``.  Editing
a file from the buffer is as easy as saying ``:b{pattern}`` where
``pattern`` is a unique part in the file name, which could be even a
single letter! This gets even simpler if you want to go back to a file
where you were a second ago, simply use ``CTRL-6``!  If you are good at
keeping track of the jumps you made don't forget to use ``CRTL-o`` and
``CRTL-i``, this will bring you home in a blink of an eye (this one is
easy to overuse, but don't be Hulk - don't smash).

Still not impressed? Here is a real case scenario. You are editing your
notes from the previous month and you have 20+ files opened in your Vim
session, you suddenly realize that it would be a great idea to add the
same hyperlink, pointing to a table of content file, at the end of every
opened files in your buffers. This very simple problem would probably be
an opening scene to a horror movie in most text editors, but in Vim all you
have to do is make a small macro called ``r``

.. code:: vim

  qrGohyperlink pew pewCTRL-[q

(``q`` - opens and saves the macro, ``r`` - is the register name, ``G``
\- go to the end of the file, ``o`` - drop into a new line,
everything in between is hyperlink content and ESC sequence). Now just
apply the macro to the buffer list

.. code:: vim

  :bufdo! normal @r

BAM!

You could also spiral down the rabbit hole and in the worlds of
splitting windows, multiple tabs and folded contents if you feel like
it...

All of this and yet we are still scratching the surface of Vim's
capabilities when it comes to editing multiple files and working with
notes. I don't want you to get me wrong, using plugins can be great.
However, certain plugins seem to reinvent some of Vim's irreplaceable
capabilities and don't seem to fit as well with other Vim's tools for
anything else than what they are designed for. Although this might not
be bad per-say, it is probably not optimal for many of us how would.


Configuration
-------------

If you are using Vim make sure that you configure your ``~/.vimrc``,
however if you are Neovim user you should make changes to in
``~/config/nvim/init.vim``.

1. Set the path of your Vim to recursively into the subdirectories with

.. code:: vim

  set path+=**

2. Enable autocompletion in the command line by

.. code:: vim

  set wildmenu

This configuration is not well-known as much as it probably should be
since it enables users to do fuzzy search [1]_. In Neovim this should be
the default, to make sure type ``:set path?`` and ``:set wildmenu?``.

3. Configure ``suffixesadd`` by adding file extension corresponding to
   the markup language, e.g., ``set suffixesadd+=.rst,.md``, if your
   going to use both reStructuredText and Markdown for taking notes.

4. It is useful to set up ``includeexpr`` (see ``:help includeexpr``).
   When eves Vim doesn't find a file, it invokes ``includeexpr`` and
   substitutes the searched pattern according to the setting. If your
   working with reStructuredText(``.rst`` files) add

.. code:: vim

  set includeexpr=substitute(substitute(substitute(v:fname,'.html','.rst',''),'^_','',''),'_$','','')

otherwise add

.. code:: vim

  set includeexpr=substitute(v:fname,'.html','.md','')

if your working with Markdown (``.md`` files).


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
other. This improves readability of both source files and HTML. To make
references to files use hyperlinks.

Here are examples with good practices that make the movement between
files simple.

.. code::

    See here, foo_ is a hyperlink and a jump point to foo.rst.

    .. _foo:: foo.html

and


.. code::

    Still `foo <foo.html>`_ is a hyperlink and a jump point to
    foo.rst but in athoer form.

In case Vim is configured according to Configuration_, place the Vim
cursor on any of the following in the text ``foo_``, ``_foo``,
``foo.html``, ``foo.rst`` or ``foo`` and press ``gf`` to jump to
``foo.rst`` (using ``:find`` with any of the names has the same effect).

This way of writing hyperlinks introduces jump points that can be used
for moving around files. Keep in mind that if ``foo.html`` exists on
Vim's path than ``foo.html`` is not a valid jump point because Vim would
jump directly to that file. However, if it doesn't exist and Vim has no
file to find ``includeexpr`` (see Configuration_) activates and makes a
substitution so that instead of ``foo.html`` Vim looks for ``foo.rst``.


Tips
----

Here are tips that could be applied to more than this project:

* Keep ``:set path+=**`` and ``:set wildmenu`` activated and start Vim
  from the top-most directory of your project. Use ``:find`` together
  with autocompletion (``TAB``) to open files inside the project.

* When opening multiple files in Vim use ``-o`` and ``-O`` flags,
  respectively, to split the windows horizontally and vertically.

* When writing text files in Vim use text wrapping ``:set textwidth=72``
  (adapt line length according to your style, e.g., Docutils uses 70
  character long lines for their documentation). Use ``gqip`` to wrap a
  paragraph on which the cursor is located or ``gq`` with visually
  selected text.


Why You Should Consider Switching to Electronic Notebooks
=========================================================

As a PhD student I came to realized that the amount of paper usage in
academia is quite high. Partly due to nature of work which revolves
around reading and writing articles and partly due to the result of
habits that we develop until we reach graduate studies to have
notebooks. However, I wouldn't say it is only me since I see many
researchers reducing the amount of paper consumption.

To support unnecessary use of paper, I started making e-notes. Although
there are web sites which provide such services (such as Evernote or
Google Keep) I value my privacy too much to give away personal
information freely. In the same time using plain text files for making
notes just doesn't cut it since the readability of ``.txt`` files is
very poor. Therefore, having more readable file formats such as HTML and
PDF would be favorable.

Even though most of people in academia are used to writing LateX,
writing ``.tex`` files is an overkill as it is tedious and time
consuming even for advanced users. This is where flexibility and ease of
markup languages like reStructuredText and Markdown starts to dominate
the well formulated structure of LaTeX. See `reStrucutredText vs.
Markdown`_ if you are unsure which markup language is better for you.


.. _`reStructuredText vs. Markdown`: https://eli.thegreenplace.net/2017/restructuredtext-vs-markdown-for-technical-documentation/ 

.. [1] Unfortunatly, this is not so well-known feature. It does not have the complete functionality of plugins such as CommandT_ and ctrlp_, but in my opinion it works great.

..  I could have went for Markdown but I chose reStrucutredText since it has more features and is, in my honest opinion, more appropriate when it comes to technical documentation (see `reStructuredText vs. Markdown`_ article).

.. [3] This is because of ``isfname`` and the list of allowed characters for filenames in Windows.

.. _CommandT: https://github.com/wincent/Command-T
.. _ctrlp: https://github.com/ctrlpvim/ctrlp.vim
