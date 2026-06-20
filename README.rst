###############################################
Dubs Vim |em_dash| HTML Character Entity Lookup
###############################################

.. |em_dash| unicode:: 0x2014 .. em dash

About This Plugin
=================

This plugin helps the developer convert ASCII to
HTML Character Entities (a/k/a Special Characters)
using either an interactive table or a prompt.

This code is a reworking of Christian Habermann's awesome
chartab.vim, which displays an interactive list of ASCII
character values. Check it out here:

| http://www.vim.org/scripts/script.php?script_id=898

I lifted the list of HTML4 Character Entities from TNT Luoma:

| http://tntluoma.com/files/codes.htm (dead link)
| http://www.dwaynecasey.com/tnt-luomas-html-codes.htm (rebirth!)

.. note:: Over the past number of years, more and more software
          recognizes Unicode, so this plugin is not as useful
          as it once was. E.g., even reStructured Text says not
          to bother with entities codes but to just use the
          actual Unicode character in the source. Now if only
          we had a nice, long list of Unicode characters from
          which to copy and paste.

.. note:: Try the built-in, ``:digraph``, to list all the
          diacritical marks. See:
          http://vim.wikia.com/wiki/Entering_special_characters
          To insert a digraph, press ``<Ctrl-L>`` followed by the two
          character combination shown under ``:digraph``. You can also
          call ``:set dg``, and then you can use a backspace to make
          digraphs, e.g., ``<Ctrl-K>a:`` could inѕtead be typed ``a<BS>:``
          Be sure to ``:set nodg`` when you're done, otherwise you'll
          surprise yourself sometimes after a backspace.

          Hint: Try ``:TabMessage digraph`` to copy and paste digraphs.

Installation
============

Installation is easy using the packages feature (see ``:help packages``).

To install the package so that it will automatically load on Vim startup,
use a ``start`` directory, e.g.,

.. code-block:: bash

    mkdir -p ~/.vim/pack/landonb/start
    cd ~/.vim/pack/landonb/start

If you want to test the package first, make it optional instead
(see ``:help pack-add``):

.. code-block:: bash

    mkdir -p ~/.vim/pack/landonb/opt
    cd ~/.vim/pack/landonb/opt

Clone the project to the desired path:

.. code-block:: bash

    git clone https://github.com/landonb/dubs_html_entities.git

If you installed to the optional path, tell Vim to load the package:

.. code-block:: vim

   :packadd! dubs_html_entities

Just once, tell Vim to build the online help:

.. code-block:: vim

   :Helptags

Then whenever you want to reference the help from Vim, run:

.. code-block:: vim

   :help dubs-html-entities

Entity Table Commands
=====================

Interactive Entity Table
------------------------

``<LocalLeader>dh`` (usually ``\dh``) displays an
interactive entity list in the current window.

You can double-click entities to copy-and-paste
them back to the buffer you were just
working on, or you can just position the cursor
over an entity and press ``r`` (or ``<Enter>``) to do
the same.

Press ``b`` or ``B`` to cycle forwards or backwards
through the set of available bases.

HTML recognizes three entity formats, e.g.,

| ``decimal:               &#928;``
| ``hexadecimal:           &#x3D6;``
| ``entity/friendly name:  &piv;``

Use ``q`` or ``<ESC>`` to quit the buffer. It will
be destroyed and the last working buffer will
be displayed instead.

Interactive Entity Lookup
-------------------------

``<LocalLeader>dH`` (usually ``\dH``) prompts you for an
ASCII character, which will be converted to its HTML
representation and pasted in place.

In the command window, you should see:

``>> Please enter a character:``

Type just the single character you want translated
and its entity reference will be inserted into
your working buffer at the cursor. (And note
that you don't have to hit return after typing
the character to be translated).

- E.g., if you enter ``&``, it'll insert ``&amp;``.

Dubs Vim Kep Mapping Reference
==============================

===========================  ============================  ==============================================================================
 Key Mapping                  Description                   Notes
===========================  ============================  ==============================================================================
 ``<LocalLeader>dh``          Toggle HTML                   Show special HTML character entity lookup.
                              Character Entity Table        You can switch between decimal, hexadecimal, and friendly names.
===========================  ============================  ==============================================================================
 ``<LocalLeader>dH``          HTML Character Entity         Prompts for a character and inserts its encoded HTML representation.
                              Prompt                        - E.g., type `&` and it'll insert ``&amp;``.
===========================  ============================  ==============================================================================

