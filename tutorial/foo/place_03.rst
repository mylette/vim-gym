.. -*- coding: utf-8 -*-

=========================
Find a Place to Jump From
=========================

Great work! You have successfully jumped into a file located in a
subdirectory using abbreviated pattern.

Now it's time to learn about *goto file* command or ``gf``. This is yet
another useful command that works in a similar way as ``:find``, but
without all that "annoying" typing. Basically, instead of typing the
pattern to ``:find`` all you have to do is move the cursor over the text
that you want to use as the pattern and while in Normal mode press
``gf``, it's that simple.

Try it out, place your cursor over the marked word --> place_04 <-- and
jump away by pressing ``gf``. But remember to come back using ``CTRL-o``
I still want to show you few things before we go further.

Did you notice that until now we worked with only one window in Vim?
This is not the ideal workflow when working with multiple files.
Therefore, if you're used to working with multiple windows you can split
the window when jumping to a file either by using a version of ``:find``
called *splitfind* ``:sfind`` (or ``:sf`` for short). Before you open
any windows which you maybe don't know how to close, here's a tip, use
``CTRL-w q`` to close the window this will return you to the previous
one. Feel free to try either

.. code:: vim

  :sf place_04.rst

to jump to the file while splitting the window horizontally (close the
window by pressing ``CTRL-w q`` and come back) or

.. code:: vim

  :vert sf place_04.rst

vertically. The same result can be accomplished with ``gf``, place the
cursor over the word that you would like to use as the pattern and press
``CTRL-w F`` (capital F). I don't want to go down the rabbit hole and
start talking about window managing, this tutorial is focused on the
movement between multiple files.

I bet you love ``gf`` by now, since it don't require much typing, so
here is a jump point for you: ``place_04``. Notice that the jump point
does not have the file path and extension, this is because ``gf`` will
expand the pattern under the cursor together with ``:set path+=**`` and
``:set suffixesadd+=.rst`` configuration into ``place_04.rst``. Place
the cursor on ``place_04`` and use ``gf`` to jump to the next topic.
