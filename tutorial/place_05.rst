.. -*- coding: utf-8 -*-

==========
The Buffer
==========

Press ``CTRL-g`` here to see where you are. You cursor way on
``place_05.html`` when you pressed ``gf`` but you actually jumped to
``place_05.rst``, and the reason behind it is your configuration for
``includeexpr``.

It's time to cover Vim's amazing buffers. When it comes to multi-file
editing this is where Vim starts to shine. Understanding how to use the
buffers significantly improves your efficiency so I highly recommend
reading ``:help buffers`` when you have the time. Buffers allow us to
open multiple files in different windows and tabs for editing.

Think of buffers as a register which (ethically) tracks your movement in
Vim. Whenever you open a new file this is registered in the buffers.
Type ``:buffers`` (or shorter ``:ls``) and it will give you a list of
files you have edited during your Vim session. If you have followed this
tutorial, your output of your ``:ls`` should look something like this::

  :ls                                                                                                                                                           
    1      "place_01.rst"                 line 55
    2      "place_02.rst"                 line 53
    4      "foo/place_03.rst"             line 47
    6 #    "place_04.rst"                 line 55
    8 %a   "place_05.rst"                 line 8

Each file has a unique number assigned to it and line at which the
cursor was before the jump. Currently edited file is marked with ``%``
and ``#`` is the file from which you came. If you look at the list, it
seems like there are files missing because some of the numbers are
missing. In the same time we see that all the files we visited are
present in the list.  The reason for this is that during this tutorial
we have opened files and than used ``CTRL-o`` to jump back and than
reopened the same files again.

Command ``:b`` allows us to move between the files in the list produced
by ``:ls`` command. In order to move to ``place_02.rst`` file you can
either specifying the unique number of that file ``:b2`` or  unique
pattern ``:b_02`` that corresponds to the file name (place**_02**.rst).

Remember when you typed ``:echo @%`` after a jump to see in which file
you were? You actually used buffers without knowing it. You can also
use ``:b#`` which means go the files where you were before entering this
file. In case you made a lot of jumps inside a file you are editing
typing ``:b#`` can be much faster to move to a previous file.
