======
pyGett
======

About
=====

This library provides a binding to the REST API for the file sharing service `Ge.tt <http://ge.tt>`_. Please see
the `Ge.tt Developer's Documentation <http://ge.tt/developers>`_ for information on how to get an API key.

Installation
============

To install, use the standard ``python setup.py install``

Quick Usage
===========

The API initializaton requires the following parameters to be present:

- **apikey**: The API key assigned by Ge.tt for your application
- **email**: The email address linked to an API key
- **password**: The password linked to an API key

Example initialization::

    from pygett import Gett

    client = Gett(
            apikey = "apitest",
            email = "apitest@ge.tt",
            password = "secret"
            )

Getting a dict of all shares::

    shares = client.get_shares()
    for file in shares['4ddfds'].files
        print file.filename

Getting a list of all shares::

    shares = client.get_shares_list()
    for share in shares:
        for file in share.files:
            print share.sharename + "\t" + file.filename + "\t" + file.size

Getting a specific share::

    share = client.get_share("4ddfds")

Getting a specific file::

    file = client.get_file("4ddfds", 0)

Uploading a file::

    file = client.upload_file(
            filename = "test.rst",
            data = open("test.rst", "rb").read()
            )

    print "File '%s' is now available at %s" % (file.filename, file.getturl)

Downloading file content::

    file = client.get_file("4ddfds", 0)
    buffer = file.contents()

Most methods return a :py:mod:`pygett.base.Gett` specific object such as :py:mod:`pygett.shares.GettShare`, 
:py:mod:`pygett.files.GettFile` or :py:mod:`pygett.user.GettUser`.

Contents
========

.. toctree::
   :maxdepth: 2

   pygett

License
=======

`MIT License <http://www.opensource.org/licenses/mit-license.php>`_

Copyright (c) 2011 Mark Allen

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and 
associated documentation files (the "Software"), to deal in the Software without restriction, including 
without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or 
sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject 
to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial 
portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT 
NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. 
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, 
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE 
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

