.. -*- coding: utf-8 -*-

=====================
Fixing ``gf`` for RST
=====================

If you are familiar with reStructuredText (RST), you might have noticed
that in the previous example we used plain text as a jump point for our
``gf`` command (i.e., ``place_04``). Otherwise, if you don't know
reStructuredText, last sentence probably confused you and you are
wondering "What's wrong with using plain text as a jump point?".

The thing is, when writing RST you will eventually want to convert all
.rst files to .html files. Like other markup languages, RST supports
hyperlink syntax making it possible to creates jump points for HTML.
Unfortunately, the hyperlink syntax in RST is not automatically a jump
point for Vim to other .rst files.

Let's assume that the names of HTML files are the same as .rst files
only with extension .html instead of .rst (i.e., file named
``place_03.rst`` becomes ``place_03.html``). In RST, a hyperlink with
the text "Jill" pointing to the content of ``foo/place_03.rst`` could be
either one of the following

.. code::

  go to `Jill <foo/place_03.html>`_

.. code::

  go to Jill_

  .. _Jill: foo/place_03.html

Without configuration to Vim it's not possible to use ``gf`` on
hyperlinks ``<foo/place_03.html>`` and ``foo/place_03.html`` and expect
Vim to jump to corresponding .rst source file ``foo/place_03.rst``. If
we tried Vim would either complain giving an error message ``Can't find
file "foo/place_03.html" in path`` or it would would jump into
``foo/place_03.html`` if this file existed, either way, this is not what
we want.

Vim has a nice toolbox for dealing with these kinds of problems and
that's configuring ``includeexpr``. If Vim fails to find the file where
you want to go, using ``:find`` or ``gf``, it will look in
``includeexpr`` and follow the rules that are provided there (see
``:help includeexpr``) which is usually some substitution. Therefore,
make sure to configure ``includeexpr`` according to README_ in order to
continue the tutorial because now you are going to jump to a .rst file
using RST hyperlink syntax. This is a really nice feature because it
allows us write in standard RST syntax and jump to the corresponding
files inside the directory of our project. So place your cursor inside
the angle brackets in the `following hyperlink <place_05.html>`_ and
press ``gf``.

.. Note::

  This doesn't work when there is a file called ``place_05.html`` inside
  your working directory. In that case Vim will find ``place_05.html``
  file, and therefore it will not invoke ``includeexpr`.

.. _README: ../README.rst
