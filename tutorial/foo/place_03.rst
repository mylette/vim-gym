.. -*- coding: utf-8 -*-

=========================
Find a Place to Jump from
=========================

Great work! You have successfully jumped into a file located in a
subdirectory.

Now it's time to learn about *go to file* command or ``gf``. This is yet
another useful command that works in a similar way as ``:find``, but
without so much typing. Basically, instead of typing the pattern to
``:find`` all you have to do is move the cursor over text which you want
to use as pattern and while in the Normal mode press ``gf``, it's that
simple.

Try it out, place your cursor over the marked word --> place_04 <-- and
jump away by pressing ``gf``. But don't run away, come back using
``CTRL-o`` I still want to show you something before we go further.

Did you notice that so far we have worked with only one window in Vim?
This is not the Vim style of doing things. Therefore, if you're used to
working with multiple windows you could chose to split the window when
making a jump either by using a version of ``:find`` called *splitfind*
``sfind`` (or ``sf`` for short). Before you open any windows here's a
tip, use ``CTRL-w q`` to close the window which will return you to the
previous one. Feel free to try either

.. code:: vim

  sf place_04.rst

which jumps to the file and splits the window horizontally (close the
window using ``CRTL-w q`` and come back) or

.. code:: vim

  vert sf place_04.rst

vertically. The same result can be accomplished with ``gf``, place the
cursor over the word that you would like to use as a pattern and press
``CTRL-w SHIFT-f``. I don't want to go down the rabbit hole and start
talking about window managing, this tutorial is focused on movement
between the files.

I bet you love ``gf`` by now, it don't require much typing, so here is a
jump point for you: ``place_04``. Notice that the jump point does not
have the file path and extension, this is because ``gf`` will expand the
pattern under the cursor together with ``set path+=**`` and ``set
suffixesadd+=.rst``). Place the cursor on the jump point and use ``gf``
to jump to the next topic.
