.. -*- coding: utf-8 -*-

====================
Back and Forth We Go
====================

Congrats, you made the jump Neo!

Take a moment, look around and see where you are. Try typing ``:echo
@%`` or pressing ``CTRL-g``, while in the Normal mode, to see where you
ended up. Spoiler alert, you came all the way from ``place_01.rst`` to
``place_02.rst``, pretty nice jump.

Vim keeps track of your cursor position so you can move back and forth
between your old jumps easily using ``CTRL-o`` and ``CTRL-i``. Thus,
instead of using ``:find`` and issuing command ``:find place_01.rst``
to go back you can do that with ``CTRL-o`` and go back to the exact
location from which you jumped into this file. Try it out, press
``CTRL-o`` but don't forget to press ``CRTL-i`` to come back.

As you can imagine, this is really useful when you need to move between
different files, instead of typing ``:find`` you can use ``CTRL-o`` and
``CRTL-i`` to jump back and forth. However, keep in mind, *by default
Vim doesn't let you jump to another file if there are unsaved changes*
because this way of jumping is equivalent to closing a file. Later you
will see a more "Vimistic" way of jumping to the previous file. Typing
``:jumps`` (or shorter ``:ju``) in the Normal mode returns the history
of your jumps (see ``:help jumps``) between which you can go back and
forth.

One thing you should know about the engine that runs ``:find`` is that
it is easily configurable. When you set your Vim environment with  ``set
path+=**`` it search recursively for all the files in the current
working directory. If the "target file" is in a subdirectory, you don't
need to specify the path to the file, just searching for the name will
be enough for Vim will find it. Try it with the ``foo/place_03.rst``
file, instead of typing the full file path search for the file name with

.. code:: vim

  :find place_03.rst

Don't forget to come back using ``CTRL-o``, we still need to cover one
more thing before going further.

Another useful configuration for ``:find`` is ``suffixesadd``. Long
story short, if you set ``:set suffixesadd+=.rst`` Vim will
automatically add suffix ".rst" to your search criteria if there are no
matches for the original pattern and try searching again. This works
really well together with ``set path+=**``. Try it for yourself, jump to
the next file by typing only

.. code:: vim

  :fin place_03

Notice that you can abbreviated ``:find`` with ``:fin``, this is also allowed.
