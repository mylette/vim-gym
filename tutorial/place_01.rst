.. -*- coding: utf-8 -*-

Make the Jump
=============

.. Attention::

  To follow the tutorial open this file in Vim/Neovim from the dierctory
  where the file is located. This ensures that the ``pwd`` in your Vim
  is set approprietly for multi-file manipulation.

Before jumping anywhere, type ``:pwd`` (without the quotes, sorry for
quotes but they are a part of reStructuredText markup language syntax)
in Normal mode to see what is your working directory. The directory in
which you were when you opened Vim is your current working directory.
Optionally, you could change it using ``:cd`` command. It's considered a
good practice to have your working directory at the top-most level of
the project on which you are working. In this case using ``:pwd`` should
return a path which ends with ``/tutorial``. This is encouraged, because
all of the files we will be working with are located in this directory
or it's subdirectories.

Typically, our files are scattered across subdirectories of our projects
but this shouldn't slow us down when working with Vim, right? In fact,
it means that we should master jumping between files [1]_ in order to
increase our productivity.

Let me introduce you to ``:find``, this command is one of your best
friends when it comes to opening and jumping into files. It works like
this, while you are in Normal mode, you would type the command together
with the *target filename* to which you would like to go to, as

.. code:: vim

  :find target_filename

Most Vim users get surprised when they learn that ``:find`` actually
supports fuzzy search without plugins. If you are using Vim all you have
to do is include ``set path=**`` and ``set wildmenu`` in your
``~/.vimrc``. For Neovim users this functionality should be default,
however if it is not just include the same configuration to your
``~/.config/nvim/init.vim``. To use the fuzzy search engine type
``:find`` and start entering the name of your *target filename* then use
``TAB`` to autocomplete the file name. Let's see ``:find`` in action.

Use ``:find`` to jump to a files called ``place_02.rst``. To do this
simply type ``:find place_02`` (without the quotes, once again sorry for
that) and press ``TAB``. Vim should expand this to ``:find
place_02.rst`` and I'll see you there.

.. [1] If this reminds you of the scene from "The Matrix" movie where
       Neo (Keanu Reeves) has to jump rooftops after Morpheus (Laurence
       Fishburne) you are awesome and we should be friends!
