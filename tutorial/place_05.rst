.. -*- coding: utf-8 -*-

===========
The Buffers
===========

Press ``CTRL-g`` to see where you are. Let me remind your, your cursor
was on ``place_05.html`` when you pressed ``gf`` but you actually jumped
to ``place_05.rst``, and the reason behind it is your configuration for
``includeexpr``. This is an amazing feature [1]_!

Now it's time to cover Vim's amazing buffers. When it comes to
multi-file editing this is where Vim starts to shine. Understanding how
to use the buffers significantly improves your efficiency so I highly
recommend reading ``:help buffers`` when you have the time. Buffers
allow us to open multiple files in different windows and tabs for
editing.

Think of the buffers as Vim register which (ethically) tracks your
movement between different files. Whenever you open a new file this is
registered in the buffers. Type ``:buffers`` (or shorter ``:ls``) and it
will give you a list of files you have edited during your Vim session.
If you have followed this tutorial, without closing your Vim in the mean
time, the output of your ``:ls`` should look something like this::

  :ls
    1      "place_01.rst"                 line 55
    2      "place_02.rst"                 line 53
    4      "foo/place_03.rst"             line 47
    6 #    "place_04.rst"                 line 55
    8 %a   "place_05.rst"                 line 8

Each file has a unique number assigned to it and line number at which
the cursor was before the jump. Currently edited file is marked with
``%`` and ``#`` is the file from which you came.

To move between the files in the buffers use command ``:b``. In order to
move to ``place_02.rst`` file you can either specifying the unique
number of that file ``:b2`` or unique pattern ``:b_02`` that corresponds
to the file name (place\ **_02**\ .rst). This is fast and practical if
your files have unique names (a unique letter is also enough but make
sure to have a space, e.g. ``:b letter``).

Remember that you typed ``:echo @%`` after a jump to see in which file
you were? You actually used buffers without knowing it. You can also use
``:b#`` which means go to the previous file. In case you made a lot of
jumps inside a file which you are editing just type ``:b#`` it will be
much faster to move to a previous file than ``CTRL-o``. Otherwise, you
can use ``:bn`` (next) and ``:bp`` (previous) to move up and down the
buffers list.

It is important to learn how to move to a non-existing file, this
corresponds to creating a file. A simple way to do it is with ``:e
filename`` which opens a new file for editing in the current window. If
there are any changes in the file Vim will ask you to save before moving
to the new file. A better way of making a new files is using ``:new`` or
``CTRL-w n`` to create a ``No name`` file that will get it's name when
you save the file for the first time using ``:w filename`` (otherwise
use ``:new filename`` to open a file called *filename*). The two latter
commands split the current window and create a new file in the same
time.

Lastly, if you would like to rename your file from inside Vim use
``:saveas filename``, this changes the name of the buffer inside the Vim
session and the name of the file to *filename*.

.. [1] See this `link <https://arjanvandergaag.nl/blog/navigating-project-files-with-vim.html>`_ for some cool use of ``includeexpr``.
