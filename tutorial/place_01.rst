.. -*- coding: utf-8 -*-

The First Jump
==============

.. Attention::

  To follow the tutorial start by openning this file in Vim/Neovim from
  the current directory. This makes sure that ``pwd`` in your Vim is set
  correctly.

Before starting, check your working directory in Vim by typing ``:pwd``,
in the Normal mode, and remember where you are. If you have entered from
the current working directory the results should end with "/tutorial".

Usually our files are scattered across different directories in our
projects but we won't let that slow us down, right? This means that we
have to master jumping between files in Vim [1]_ to increase our
productivity.

Let me introduce you, command ``:find`` is one of your best friends when
it comes to jumping between files. While in the Normal mode, type the
command together with the "destination file" to which you would like to
go to

.. code:: vim

  :find destination_file

To make ``:find`` search fuzzy just include ``set path=**`` and ``set
wildmenu`` in your ``~/.vimrc``. In Neovim this should be the default
but in case it isn't just include it in your ``~/.config/nvim/init.vim``
[2]_. To use the fuzzy search press ``TAB`` to autocomplete your
"destination file" name if it exists in your directory. Before you ask,
yes it works for nested directories.

Your task is to use the newly gained power of ``:find`` and jump to a
files called ``place_02.rst`` by typing

.. code:: vim

  :find place_02.rst

and I'll see you there.

.. [1] If this reminds you of the scene from "The Matrix" movie where
       Neo (Keanu Reeves) has to jump rooftops after Morpheus (Laurence
       Fishburne) you and me would probably be best friends.

.. [2] This configuration does not provide complete functionality of
       plug-ins such as CommandT_ and ctrlp_ but does the job.

.. _CommandT: https://github.com/wincent/Command-T
.. _ctrlp: https://github.com/ctrlpvim/ctrlp.vim
