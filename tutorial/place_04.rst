.. -*- coding: utf-8 -*-

========================================
Beyond the Standard ``:find`` and ``gf``
========================================

.. note::

  ``:find`` and ``gf`` can open both local and remote URL. This means
  that you can type ``:find https://neovim.io/`` (with slash in the end)
  and Vim will open HTML content of Neovim website (see ``:help netrw``
  if your interested).

So far, you have seen that it is possible to modify ``path``,
``wildmenu`` and ``suffixesadd`` to change the behaviour of ``:find``
and ``gt``.

Additional modifications to the search engine are made through
``includeexpr`` (see ``:help includeexpr``). When Vim doesn't find the
pattern you searched for it returns an error. If ``includeexpr`` is set
Vim reuses the searched pattern and changes it according to the
substitution rules in ``includeexpr`` and then runs the search again
with modified search pattern. Keep in mind that the substitution happens
only if the primary searched pattern is not found.

This functionality is practical for redirecting jumping points. For
example

.. code::

  this is a `hyperlink <foo/place_03.html>`_ to foo/place_03.html

and

.. code::

  this is a [hyperlink](foo/place_03.html) to foo/place_03.html

are hyperlinks in reStructuredText and Markdown that point to
``foo/place_03.html``. By configuring ``includeexpr`` you can make a
substitution rule which searches for ``basename.rst`` file instead of
``basename.html`` file. In the example shown above Vim searches for
``foo/place_03.rst`` whenever ``:find`` or ``gf`` are used on
``foo/place_03.html``.

To continue with the tutorial make sure to configure ``includeexpr``
according to README_ configuration for .rst files because you are going
to jump to a .rst file using RST hyperlink syntax. Place your cursor
inside the angle brackets in the `following hyperlink <place_05.html>`_
and press ``gf``.

.. Note::

  This doesn't work when there is a file called ``place_05.html`` inside
  your working directory. In that case Vim will find ``place_05.html``
  file, and therefore will not invoke ``includeexpr``.

.. _README: ../README.rst#configuration
