Meta Package Manager
====================

A CLI and a `BitBar <https://getbitbar.com>`_ plugin to simplify software
upgrades from several package managers.

Stable release: |release| |versions| |license| |dependencies|

Development: |build| |coverage| |quality|

.. |release| image:: https://img.shields.io/pypi/v/meta-package-manager.svg
    :target: https://pypi.python.org/pypi/meta-package-manager
    :alt: Last release
.. |versions| image:: https://img.shields.io/pypi/pyversions/meta-package-manager.svg
    :target: https://pypi.python.org/pypi/meta-package-manager
    :alt: Python versions
.. |license| image:: https://img.shields.io/pypi/l/meta-package-manager.svg
    :target: https://www.gnu.org/licenses/gpl-2.0.html
    :alt: Software license
.. |dependencies| image:: https://img.shields.io/requires/github/kdeldycke/meta-package-manager/master.svg
    :target: https://requires.io/github/kdeldycke/meta-package-manager/requirements/?branch=master
    :alt: Requirements freshness
.. |build| image:: https://img.shields.io/travis/kdeldycke/meta-package-manager/develop.svg
    :target: https://travis-ci.org/kdeldycke/meta-package-manager
    :alt: Unit-tests status
.. |coverage| image:: https://codecov.io/github/kdeldycke/meta-package-manager/coverage.svg?branch=develop
    :target: https://codecov.io/github/kdeldycke/meta-package-manager?branch=develop
    :alt: Coverage Status
.. |quality| image:: https://img.shields.io/scrutinizer/g/kdeldycke/meta-package-manager.svg
    :target: https://scrutinizer-ci.com/g/kdeldycke/meta-package-manager/?branch=develop
    :alt: Code Quality

.. figure:: http://imgs.xkcd.com/comics/universal_install_script.png
    :alt: Obligatory XKCD.
    :align: right
    
    Source: `XKCD #1654 <https://xkcd.com/1654/>`_.


Supported
---------

Only macOS platform is supported.

================  ===================  =============
Package manager   Individual upgrade   Full upgrade
================  ===================  =============
|homebrew|__      ✅                   ✅
|cask|__          ✅                   ✅
|pip2|__          ✅                   ✅
|pip3|__          ✅                   ✅
|npm|__           ✅                   ✅
|apm|__           ✅                   ✅
|gem|__           ✅                   ✅
|mas|__           ✅                   ✅
================  ===================  =============

.. |homebrew| replace::
   Homebrew
__ http://brew.sh
.. |cask| replace::
   Homebrew Cask
__ https://caskroom.github.io
.. |pip2| replace::
   Python 2 ``pip``
__ https://pypi.org
.. |pip3| replace::
   Python 3 ``pip``
__ https://pypi.org
.. |npm| replace::
   Node's ``npm``
__ https://www.npmjs.com
.. |apm| replace::
   Atom's ``apm``
__ https://atom.io/packages
.. |gem| replace::
   Ruby's ``gem``
__ https://rubygems.org
.. |mas| replace::
   Mac AppStore via ``mas``
__ https://github.com/argon/mas

If you're bored, feel free to add support for new package manager. See the
`list of good candidates
<https://en.wikipedia.org/wiki/List_of_software_package_management_systems>`_.


Usage
-----

Examples of the package's ``mpm`` CLI.

List global options and commands:

.. code-block:: bash

    $ mpm
    Usage: mpm [OPTIONS] COMMAND [ARGS]...

      CLI for multi-package manager updates and upgrades.

    Options:
      -v, --verbosity LEVEL  Either CRITICAL, ERROR, WARNING, INFO or DEBUG
      --version              Show the version and exit.
      --help                 Show this message and exit.

    Commands:
      list      List available updates.
      managers  List supported package managers and their location.


List all supported package managers and their status on current system:

.. code-block:: bash

    $ mpm managers
    ╒═══════════════════╤══════════╤═════════════════════╕
    │ Package manager   │ Active   │ Location            │
    ╞═══════════════════╪══════════╪═════════════════════╡
    │ Cask              │ ✅        │ /usr/local/bin/brew │
    ├───────────────────┼──────────┼─────────────────────┤
    │ Homebrew          │ ✅        │ /usr/local/bin/brew │
    ├───────────────────┼──────────┼─────────────────────┤
    │ Mac AppStore      │ ✅        │ /usr/local/bin/mas  │
    ├───────────────────┼──────────┼─────────────────────┤
    │ Python 2 pip      │ ✅        │ /usr/local/bin/pip2 │
    ├───────────────────┼──────────┼─────────────────────┤
    │ Python 3 pip      │ ✅        │ /usr/local/bin/pip3 │
    ├───────────────────┼──────────┼─────────────────────┤
    │ Ruby Gems         │ ✅        │ /usr/local/bin/gem  │
    ├───────────────────┼──────────┼─────────────────────┤
    │ apm               │ ✅        │ /usr/local/bin/apm  │
    ├───────────────────┼──────────┼─────────────────────┤
    │ npm               │ ✅        │ /usr/local/bin/npm  │
    ╘═══════════════════╧══════════╧═════════════════════╛


BitBar plugin
-------------

.. image:: https://raw.githubusercontent.com/kdeldycke/meta-package-manager/develop/screenshot.png
    :alt: Bitbar plugin screenshot.
    :align: left


History
-------

The ``package_manager.py`` script `started its life in my 'dotfile' repository
<https://github.com/kdeldycke/dotfiles/commit/bfcc51e318b40c4283974548cfa1712d082be121#diff-c8127ac6af9d4a21e366ff740db2eeb5>`_,
as a rewrite from Bash to Python of the `'brew-updates.sh' script
<https://getbitbar.com/plugins/Dev/Homebrew/brew-updates.1h.sh>`_.

I then `merged both Homebrew and Cask
<https://github.com/kdeldycke/dotfiles/commit/792d32bfddfc3511ea10c10513b62e269f145148#diff-c8127ac6af9d4a21e366ff740db2eeb5>`_
upgrade in the same single script as both were `competing with each other
<https://github.com/matryer/bitbar-plugins/issues/493>`_ when run concurrently.

I finally `proposed the script for inclusion
<https://github.com/matryer/bitbar-plugins/pull/466>`_ in the official `BitBar
plugin repository <https://github.com/matryer/bitbar-plugins>`_. It lived there
for a couple of weeks and saw a huge amount of contributions by the community.

With its complexity increasing, it was `decided to move the plugin
<https://github.com/matryer/bitbar-plugins/issues/525>`_ to `its own repository
<https://github.com/kdeldycke/meta-package-manager>`_. For details, see the
`migration script
<https://gist.github.com/kdeldycke/13712cb70e9c1cf4f338eb10dcc059f0>`_.


Current status
--------------

Active development of the script is continuing here, in the exact same
conditions as we were before moving the repository, like nothing happened.

Each time we reach a releaseable script, we simply tag it and push a copy to
the BitBar plugin repository. Plain and simple.

At the same time we maintain a Python library on the side. The library is going
to handle all idiosyncracies of supported package managers under a unified API.

Once the library is good enough, we'll evaluate rebasing the original plugin on
it, and lay out a plan for a painless transition, from the standalone script to
a bare BitBar-plugin depending on the library alone.

In the mean time we have to temporarily manage duplicate code. But at least the
whole project is kept in one centralized place, trying to tackle the same
issues.


Contributors
------------

* `Kevin Deldycke <https://github.com/kdeldycke>`_
* `Brian Hartvigsen <https://github.com/tresni>`_


License
-------

This software is licensed under the `GNU General Public License v2 or later
(GPLv2+)
<https://github.com/kdeldycke/meta-package-manager/blob/master/LICENSE>`_.
