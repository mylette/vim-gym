==============================
Notes in Vim + Markup Language
==============================

:Author: Velibor Zeli
:Copyright: This tutorial has been placed in the public domain.

.. contents::

If you are here that means that you are aware of how amazing Vim is for
text manipulation and there is no need for me to add more to it.

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

It's easy to lose track of the opened files but rest assured that the
Vim buffer keeps a list for you, all you need to do is ask ``:ls``.
Editing a file from the buffer is as easy as saying ``:b{pattern}``
where ``pattern`` is the unique part in the file name, which could be
even a single letter! This gets even simpler if you want to go back to a
file where you were a second ago, simply use ``CTRL-6``!  If you are
good at keeping track of the jumps you made don't forget to use
``CRTL-o`` and ``CRTL-i``, this will bring you home in a blink of an eye
(but don't overuse this one).

Still not impressed? Here is a real case scenario. You are editing your
notes from the previous days and you have 20+ files opened in your Vim
session, you suddenly realize that it would be a great idea to add the
same hyperlink, pointing to a table of content file, at the end of every
opened files in your buffers. This very simple problem would probably be
an opening scene to a horror movie in most of editor, but in Vim all you
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
notes. Using plugins is awesome, I don't want you to get me wrong.
Certain plugins, however, seem to reinvent some of Vim's irreplaceable
capabilities and don't seem to scale as well for anything else than what
they are designed for. Although this might not bad per say, it is probably
not optimal for many of us at.

Configuration
-------------

If you are using Vim make sure that you configure your ``~/.vimrc``,
however if you are Neovim user you should make changes to
in ``~/.config/nvim/init.vim``.

Set the path of your Vim to recursively into the subdirectories with

.. code:: vim

  set path+=**

and enable autocompletion in the command line by

.. code:: vim

  set wildmenu

It seems like in Neovim these two commands are set by default, but it
wouldn't hurt to put it in there just in case. This configuration
enables fuzzy search, however, be aware that it does not have the
complete functionality of plugins such as CommandT_ and ctrlp_.

.. _CommandT: https://github.com/wincent/Command-T
.. _ctrlp: https://github.com/ctrlpvim/ctrlp.vim

When write notes one works with a lot of files of the same file type (in
this case .rst [1]_). It is helpful if Vim adds 

.. [1] I could have went for Markdown but I chose reStrucutredText since
       it has more features and is, in my honest opinion, more
       appropriate when it comes to technical documentation (see
       `StructuredText vs. Markdown`_ article).

.. _`StructuredText vs. Markdown`: https://eli.thegreenplace.net/2017/restructuredtext-vs-markdown-for-technical-documentation/
