.. -*- coding: utf-8 -*-

Make the Jump
=============

.. Attention::

  To follow the tutorial open this file in Vim/Neovim from the dierctory
  where the files is located. This ensures that the ``pwd`` in your Vim
  is set approprietly for multi-file manipulation.

Before you jump anywhere, type ``:pwd`` (without the quotes, sorry for
quotes but they are a part of the reStructuredText markup language)
while your are in the Normal mode to see what is your working directory.
The directory in which you were when you opened Vim is your current
working directory. Optionally, you could change it using ``:cd``
command. It's considered a good practice to have your working directory
at the top-most level of the project on which you are working. In this
case ``:pwd`` should return a path which ends with ``/tutorial`` because
all of the files we will be work with are located in this directory or
it's subdirectories.

Typically, our files are scattered across subdirectories of our projects
but this shouldn't slow us down when working with Vim, right? In fact,
it means that we should master jumping between files [1]_ in order to
increase our productivity.

Let me introduce you to ``:find``, this command is one of your best
friends when it comes to opening and jumping into files. It works like
this, while you are in the Normal mode, you would type the command
together with the *target filename* to which you would like to go to, as

.. code:: vim

  :find target_filename

Most Vim users get surprised when they learn that ``:find`` actually
support fuzzy search without plugins. If you are using standard Vim all
you have to do is include ``set path=**`` and ``set wildmenu`` in your
``~/.vimrc``. For Neovim users this functionality should be default,
however if it is not just include the same configuration to your
``~/.config/nvim/init.vim`` [2]_. To use the fuzzy search engine type
``:find`` and start entering the name of your *target filename* then use
``TAB`` to autocomplete the file name. Let's see ``:find`` in action.

Use your ``:find`` and jump to a files called ``place_02.rst``. To do
this simply type ``:find place_02.rst`` (without the quotes, once again
sorry for that) and I'll see you there.

.. [1] If this reminds you of the scene from "The Matrix" movie where
       Neo (Keanu Reeves) has to jump rooftops after Morpheus (Laurence
       Fishburne) we would probably be best friends.

.. [2] This configuration does not have the complete functionality of
       plugins like CommandT_ and ctrlp_, but it provides the
       fundamentals which is usually sufficiend.

.. _CommandT: https://github.com/wincent/Command-T
.. _ctrlp: https://github.com/ctrlpvim/ctrlp.vim
