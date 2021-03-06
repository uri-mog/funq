The *funq* project
==================

**funq** is a tool to write FUNctional tests for Qt applications
using python.

It is licenced under the CeCILL v2.1 licence (very close to the GPL v2).
See the LICENCE.txt file distributed in the sources for more information.

The licence may appear restrictive, but as **funq** is a testing tool, you
probably just don't mind. Do not deliver funq alongside your code source
or compiled binaries if your licence is not compatible, that's all. You can
still use the sources, or link with funq libraries for a personal use
(like testing!).

Please feel free to contribute to this project by creating github issues,
pull requests, or simply staring the project! It will be greatly appreciated.

Tutorial and documentation:

.. image:: https://readthedocs.org/projects/funq/badge/?version=latest
    :target: http://funq.readthedocs.org

Travis-ci build:

.. image:: https://travis-ci.org/parkouss/funq.svg?branch=master
    :target: https://travis-ci.org/parkouss/funq

Get funq on PyPi (server and client packages):

.. image:: https://pypip.in/version/funq-server/badge.png
    :target: https://pypi.python.org/pypi/funq-server/

.. image:: https://pypip.in/version/funq/badge.png
    :target: https://pypi.python.org/pypi/funq/

How does *funq* works
=====================

**funq** is divided in two parts:

- **funq-server** is the server part of the project, composed of an
  executable called **funq** and a dynamic library **libFunq**. The
  **funq** executable allows to inject some code in a Qt application
  to start a TCP server that will allow to interact with the application.
  This is currently not working well on windows, but you can still
  build you application with libFunq as a workaround.

- **funq** is a python package that offers an API to interact with a
  **libFunq** TCP server. It is the client side of the project, and uses
  nosetests to launch FUNctional Qt tests.

Known restrictions
==================

Funq currently works with python >= 2.7 (it is fully compatible with python 3),
Qt4 and Qt5 on GNU/Linux.

It also works on Windows, but the tested application have to be compiled
with libFunq (I am not able to do a fully working dll injection for this
platform, windows expert you're welcome!).

Installation
============

You can easily install it from PyPi with pip or setuptools::

  pip install funq-server
  pip install funq

.. note::

  Note that funq-server will need qmake to build the C++ part of the server,
  and this installation will be Qt-compatible with the same Qt version of
  qmake.

  To specify the path to qmake, you can define the **FUNQ_QMAKE_PATH**
  environment variable: ::

    FUNQ_QMAKE_PATH=/usr/bin/qmake-qt5 pip install funq-server

  Also, if you're not using virtualenv you may have to take root
  privileges to install **funq**.

You can instead get the sources and install it::

  cd funq/
  pip install server
  pip install client

.. note::

  For contributors, you may want to use **pip install -e** instead of
  **pip install** commands. Note that **virtualenv** is highly recommended,
  so you can easily manage multiple python2/python3/Qt4/Qt5 environments.

.. note::

  When installing funq-server from sources, you can create a server/setup.cfg
  file to specify the qmake path::

    [build_libfunq]
    qmake_path = /usr/bin/qmake-qt5

  before running the *pip install* command, or use the **FUNQ_QMAKE_PATH**
  environment variable.

Thanks to
=========

Thanks to Yann De Poulpiquet <yann_de_poulpiquet@bestmail.us> and
Riad Lezzar <rlezzar@gmail.com> to have contributed by writing the firsts
functional tests with **funq**.

Thanks also to Jean-Luc Rouzoul, Dominique Constant and Mickaël Guérin for
having supported this project.

Without them, **funq** would never have become a free software !
