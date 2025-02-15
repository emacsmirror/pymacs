Pymacs
======

|Build Status|

.. |Build Status| image:: https://github.com//pymacs2/Pymacs/workflows/Makefile%20CI/badge.svg
    :target: https://github.com/pymacs2/Pymacs

Pymacs Notes

    :Author: François Pinard
    :Maintainer: Dennis Gentry

.. contents::

Pymacs is a powerful tool which, once started from Emacs, allows
both-way communication between Emacs Lisp and Python.  Pymacs aims
Python as an extension language for Emacs rather than the other way
around, and this asymmetry is reflected in some design choices.
Within Emacs Lisp code, one may load and use Python modules.  Python
functions may themselves use Emacs services, and handle Emacs Lisp
objects kept in Emacs Lisp space.

See below for translation credits (`Belorussian <https://web.archive.org/web/20110202105549/http://www.movavi.com/opensource/pymacs-be>`_, `Deutsche <https://web.archive.org/web/20130822054524/http://uhrenstore.de/blog/readmedateifurpymacs>`_)

1 Installation
--------------

There is a new (as of May 2017, updated Sept 2023) shell script that
installs Pymacs into a virtual environment, if you have one activated,
or into the system python (with --user) if not.  Type the following
commands into your shell:

.. code:: shell

    wget https://github.com/Pymacs2/Pymacs/raw/master/install-pymacs.sh

If you don't have wget (e.g., MacOS before \`brew install wget\`) you can use:

.. code:: shell

    curl -L -O https://github.com/Pymacs2/Pymacs/raw/master/install-pymacs.sh

Then execute the script with:

.. code:: shell

    chmod +x install-pymacs.sh
    ./install-pymacs.sh

The script is a distillation of all the installation advice I've found in
various blog posts, etc.  It installs ``rope``, ``ropemacs``, and ``Pymacs``, runs
Pymacs' tests, and ultimately checks that Pymacs works, with
``python -c`` '``import Pymacs``'.

Also, the following links are old, but now point to the most recent archived
version of François Pinard's website that seemed to contain these files:

The Pymacs manual (either in `HTML format <http://web.archive.org/web/20100706203836/http://pymacs.progiciels-bpi.ca:80/pymacs.html>`_ or `PDF format <http://web.archive.org/web/20100706203836/http://pymacs.progiciels-bpi.ca:80/pymacs.pdf>`_) has
installation instructions, a full description of the API, pointers to
documented examples, to resources, and to other Pymacs sites or
projects.  The distribution also includes the Poor's Python
Pre-Processor (**pppp**) and its manual (either in `HTML format <http://web.archive.org/web/20100706203836/http://pymacs.progiciels-bpi.ca:80/pppp.html>`_ or
`PDF format <http://web.archive.org/web/20100706203836/http://pymacs.progiciels-bpi.ca:80/pppp.pdf>`_).

2 Source
--------

Source files and various distributions are available at
`https://github.com/Pymacs2/Pymacs/ <https://github.com/Pymacs2/Pymacs/>`_.  Please report problems, comments
and suggestions to `Dennis Gentry <mailto:dennis.gentry@gmail.com>`_.

3 Known translations:
---------------------

.. table::

    +-----------+-------------------------------------------------------------+---------------------------------------------------------------+------------------+
    | Document  | Language                                                    | Translator                                                    | Date             |
    +===========+=============================================================+===============================================================+==================+
    | This file | `Belorussian <http://www.movavi.com/opensource/pymacs-be>`_ | `Paul Bukhovko <mailto:bukhovko@gmail.com>`_                  | \                |
    +-----------+-------------------------------------------------------------+---------------------------------------------------------------+------------------+
    | This file | `German <http://uhrenstore.de/blog/readmedateifurpymacs>`_  | `Anastasiya Romanova <mailto:romanova.anastasyia@gmail.com>`_ | [2012-04-09 Mon] |
    +-----------+-------------------------------------------------------------+---------------------------------------------------------------+------------------+

4 Release Notes
---------------

4.1 Notes for 0.26
~~~~~~~~~~~~~~~~~~

 _`2017-07-10`  [2017-07-10 Mon]  New release.

Pymacs 0.26 is available at its new location:

- Tarball at `https://github.com/dgentry/Pymacs/tarball/v0.26 <https://github.com/dgentry/Pymacs/tarball/v0.26>`_

- Zipped tarball at `https://github.com/dgentry/Pymacs/zipball/v0.26 <https://github.com/dgentry/Pymacs/zipball/v0.26>`_

The changes are:

- New maintainer and location because, very sadly, François Pinard died in
  April 2014.  Switched references to the archived version of the website
  because the original is offline.

- There is a new (much simpler for most people) way to install Pymacs,
  ``install-pymacs.sh``.  It performs the combined setup tasks that were the
  subject of many blog posts.  If I missed something, please let me know or
  create a pull request.

- A couple of improvements to the internal tests.

4.2 Notes for 0.25
~~~~~~~~~~~~~~~~~~

 _`2012-05-07`  [2012-05-07 Mon]  Hi everybody.

Pymacs 0.25 is now available.  You may fetch it as one of:

- `https://github.com/pinard/Pymacs/tarball/v0.25 <https://github.com/pinard/Pymacs/tarball/v0.25>`_

- `https://github.com/pinard/Pymacs/zipball/v0.25 <https://github.com/pinard/Pymacs/zipball/v0.25>`_

depending on if you want a *tar* or *zip* archive.

The installation process was modified:

- Python 3 is now supported.  This required new installation
  mechanics, and a Python pre-processor written for the circumstance
  (named **pppp**).

- Pymacs now installs a single Python file instead of a Python
  module.  This does not affect users — except maybe a few who chose
  to depend on undocumented internals.

The specifications are pretty stable.  A few additions occurred:

- Variable **pymacs-python-command** may select which Python interpreter
  to use.

- A **pymacs-auto-restart** variable lets the user decide what to do if
  the Pymacs helper aborts.

- The **Let** class got a **pops** method which pops everything in a single
  call.

- A new API function **pymacs-autoload** serves lazy imports.

There also are miscellaneous changes:

- Some errors have been corrected, both in the code and in the
  manual.

- The Emacs Lisp source has been massaged so to become uploadable in
  ELPA's (Emacs Lisp Packages Archives).

XEmacs support seems to be broken, and Jython 2.2 support does not
work yet.  As I am not much of a user of either, this is kept on ice
currently.  Interested collaborators and testers, contact me if you
feel like pushing in these areas!

Nice thanks to Pymacs contributors.  It was much fun working with you
all!

4.3 Notes for 0.24
~~~~~~~~~~~~~~~~~~

Whenever I tag a version ``-betaN`` or such, it might not be fully ready
for public distribution, this is a welcome defect that ELPA cannot
grok such versions.  Someone wanting to upload Pymacs nevertheless
found his way around the limitation by renaming the version, I guess
from ``0.24-beta2`` to ``0.24``.  Undoubtedly, it would have been polite to
check with me first… As beta releases come before real releases, it
should really have been ``0.23``.  Anyway, Marmelade now has a Pymacs
0.24.  For avoiding any more confusion, I'm skipping ``0.24`` — such a
version does not officially exist.

4.4 Notes for 0.23
~~~~~~~~~~~~~~~~~~

 _`2008-02-15`  [2008-02-15 Fri]  Hello to everybody, and Emacs users in
the Python community.

Here is Pymacs 0.23!  There has been a while, so I advise current
Pymacs users to switch with caution.  All reported bugs have been
squashed, if we except one about Emacs quit (**C-g**) not being obeyed
gracefully.  A few suggestions have been postponed, to be pondered
later.

The manual is now in reST format, and everything Allout is gone.
Postscript and PDF files are not anymore part of the distribution, you
may find them on the Web site, or use the Makefile if you have needed
tools.  Examples have been moved out of the manual into a new contrib/
subdirectory, which also holds a few new contributions.  The example
of a Python back-end for Emacs Gnus has been deleted.

Python 1.5.2 compatibility has been dropped; use Python 2.2 or better.
The Pymacs manual explains installation procedure, now simplified.
The pymacs-services script is gone, this should ease installing Pymacs
on MS Windows.  There is also a small, still naive validation suite.

The communication protocol has been revised: more clarity, less magic.
Zombie objects are less dreadful by default.  The API now supports
False and True constants, and Unicode strings (within limits set by
Emacs).

Special thanks to those who helped me at creating or testing this
release.

5 Informal notes
----------------

5.1 _`2012-05-06`  python-mode.el difficulty
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[2012-05-07 Mon]  After I recently acquired a new machine and installed
a flurry of software on it, I was saluted with:

::

    pymacs-report-error: Pymacs helper did not start within 30 seconds


The problem turns out to come from **python-mode.el** (a development
copy), which insists on providing and using its own older copy of
Pymacs.  The problem shows in the Pymacs communication buffer: a
failed attempt at importing ``Pymacs/__init__.py``.  Indeed, this file
does not exist anymore.  Pymacs now stands as a single file on the
Python side, not as a module.  This yields confusion at run time.  The
problem vanishes if I comment out **python-mode.el** initialization, or
more simply (thanks `holmboe <https://github.com/holmboe>`_) if **py-load-pymacs-p** is set to **nil**.  I'll
talk to Andreas Röhler about this.

5.2 _`2012-05-07`  Using packagers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[2012-05-07 Mon]  `Gleb Peregud <https://github.com/gleber>`_ suggests `on GitHub <https://github.com/pinard/Pymacs/issues/18>`_ that we prepare an
ELPA/Marmalade package for Pymacs.  There is also a Python side to be
addressed, and I've been lucky enough to recently meet Éric Araujo,
the **distutils2** / **packaging** maintainer.  The time might be proper to
push a bit on the idea on getting Pymacs on installers.

I saved a few notes on `Emacs Packaging <Emacs.rst>`_.  After having pondering them,
I'll follow Gleb's advice, at least to get started and experiment.
Emacs packagers do not care about Python, and Python packagers ignore
Emacs Lisp installation problems.  The pre-processing step in Pymacs
is another source of concern.  In a word, I'll save the bottle of
champagne for some later time! ☺

There is some complexity in installers, both on Emacs and Python
sides.  It's quite amusing: proponents of either side want an
installer, and dismiss as trivial the problem of installing the other
side.  Emacs users tell me: *Set PYTHONPATH approprietely and forget about it*.  Python users tell me: *Just put pymacs.el somewhere it will work, or ask the user*.  My feeling is that to do nicely implies both
an Emacs installer and a Python installer.  There is difference of
perspective as well: for users, simplicity means *both*; for the
maintainer, simplicity means *neither* ☺.
