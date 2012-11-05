========================
collective.xmpp.buildout
========================

Introduction
============

``collective.chat.buildout`` provides a helper buildout to enable you to deploy
`XMPP`_-enabled add-ons for Plone.

Currently it includes three XMPP add-ons.

* `collective.xmpp.core`_ which integrates XMPP into Plone (zero user-facing
  "features").
* `collective.xmpp.collaborate`_ which provides collaborative editing, and
* `collective.xmpp.chat`_ which provides instant messaging.

More XMPP add-ons will be adoded as they are being developed for Plone.

XMPP server and reverse proxy
=============================

This buildout will also install the '`ejabberd`_ XMPP server and `Nginx`_ to
serve as a reverse proxy for ejabberd's connection manager (the connection
manager provides a bridge between the XMPP server and the browser which speaks
HTTP).

For ejabberd you'll need to have erlang installed.

Creating the XMPP admin user
============================

``collective.chat.core`` requires an admin XMPP user to be able to register new
XMPP users whenever new Plone users are created.

In your buildout folder, after running the buildout, you need to do the following:

    ./bin/ejabberdctl register admin localhost your_password

Test that you can access your ejabberd by logging to the admin interface (typically ``http://localhost:5280/admin``). You should also be able to access the ``http-bind`` interface (of the connection manager) at ``http://loalhost:5280/http-bind``.


Installation on Debian/Ubuntu/etc.
==================================

This buildout compiles Nginx and Ejabberd from source and to do this, you'll need
the development files of their dependencies.

This is what I needed to install on a fresh(ish) Ubuntu 12.04:

    sudo apt-get install zlib1g-dev erlang lbzip2 libzip-dev libbz2-dev libxml2-dev libxslt-dev libpcre3-dev libexpat1-dev libssl-dev 

Installation on Mac OS
======================

Prerequisites:

* Erlang (e.g. ``brew install erlang`` with `homebrew`_)
* PCRE library (e.g. ``brew install pcre`` with `homebrew`_)

Then use the ``macos.cfg`` buildout configuration (``bin/buildout -c macos.cfg``).


.. _XMPP: http://xmpp.org
.. _ejabberd: ejabberd.im
.. _collective.xmpp.core: http://github.com/collective/collective.xmpp.core
.. _collective.xmpp.collaborate: http://github.com/collective/collective.xmpp.collaborate
.. _collective.xmpp.chat: http://github.com/collective/collective.xmpp.chat
.. _homebrew: http://mxcl.github.com/homebrew/
.. _nginx: http://nginx.org/
