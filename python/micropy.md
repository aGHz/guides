&#181;.py
====

&#181;.py (Micro.py, upy) is an alternative approach to building [web applications in Python](http://www.python.org/dev/peps/pep-3333/)
based on nascent philosophies in the Javascript world (c.f. [microjs](http://microjs.com/) and [Ender](http://ender.no.de/)),
as well as the guiding principle behind Linux development (_Small applications that do one thing and do it well_).
The driving idea is to eschew full-stack frameworks in favour hand-picked, extremely specialized and efficient packages.
It has a lot in common with the [TurboGears](http://turbogears.org/) philosophy of selecting best-of-breed packages,
but differs radically in the approach to bringing these packages together. Where TurboGears provides a technical
solution in the form of a full-stack framework integrating them, micro.py aims for a social approach.
The goal is to provide a curated list of micro packages, extensive guides on using them and combining them
with each other, as well as comparison studies between equivalent packages. The responsibility for decisions and
implementation details are then left to the developer.


Components
==========
A package appearing in this list does not imply a recommendation, some are merely listed for further investigation or as examples of what the component should accomplish.

Outside the app
---------------
* [Nginx](http://wiki.nginx.org/Main)
* [uWSGI](http://projects.unbit.it/uwsgi/wiki/Doc)
* [supervisord](http://supervisord.org/), [circus](http://circus.readthedocs.org/en/latest/)
* [Fabric](http://docs.fabfile.org/)
* [Git](http://git-scm.com/book), [git-flow](https://github.com/nvie/gitflow) and [GitHub](http://github.com)
* codebase directory structure inspired by the [Filesystem Hierarchy Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
  for self-contained, easily-deployable app environments
* testing: [nose](http://wiki.python.org/moin/PythonTestingToolsTaxonomy) and [nose plugins](https://nose-plugins.jottit.com/), [Python Testing Tools Taxonomy](http://wiki.python.org/moin/PythonTestingToolsTaxonomy)

Inside the app
--------------
Core functionality
* a WSGI middleware stack manager (for an easily configurable stack of middleware with automatic dependency ordering).
  If &#181;.py develops into something more concrete than a philosophy, this will likely be the most essential functionality,
  acquiring micro packages and organizing them properly both in the codebase and at runtime.
  Inspired by [Django middleware](https://docs.djangoproject.com/en/dev/topics/http/middleware/).
* a dispatcher to map URLs to Python code: [Colubrid](http://wsgiarea.pocoo.org/colubrid/documentation/),
  [Crank](https://bitbucket.org/percious/crank/) the generalized object dispatch used in [TurboGears 2](https://groups.google.com/forum/?fromgroups=#!topic/turbogears-trunk/uuGO3FQoy6g).
* a WSGI request and response convenience wrapper: [WebOb](http://docs.webob.org/en/latest/reference.html)
* request-local module globals: [paste.registry](http://pythonpaste.org/modules/registry.html) is discontinued, [Flask request context](http://flask.pocoo.org/docs/reqcontext/)
* database access: [SQLAlchemy](http://www.sqlalchemy.org/), [MongoEngine](http://mongoengine.org/), [PyMongo](http://api.mongodb.org/python/current/)
* template rendering: [Jinja2](http://jinja.pocoo.org/docs/), [Mako](http://docs.makotemplates.org/en/latest/index.html)

Optional functionality
* cache and session management: [Beaker](http://beaker.readthedocs.org/en/latest/index.html)
* HTML form validation: [FormEncode](http://www.formencode.org/en/latest/index.html), [WTForms](http://wtforms.simplecodes.com/docs/),
  [StackOverflow thread](http://stackoverflow.com/questions/3192747/recommendation-for-python-form-validation-library)
* authentication and authorization: [LibAuthKit](http://pypi.python.org/pypi/LibAuthKit), [repoze.who](http://docs.repoze.org/who/2.0/)+[.what](http://what.repoze.org/docs/1.0/)
* observer pattern (aka. signal/slot): [Louie](https://github.com/11craft/louie/), [PyDispatcher](http://pydispatcher.sourceforge.net/), [Wikipedia list](http://en.wikipedia.org/wiki/Observer_pattern#Python) of other observer packages
* automatic admin interface generation: [Sprox](http://sprox.org/),
  [Appengine Admin](http://code.google.com/p/appengine-admin/),
  [django.contrib.admin](https://docs.djangoproject.com/en/1.4/ref/contrib/admin/)
* admin shell: [IPython](http://ipython.org/documentation.html)
* CLI tool creation: [Marrow Scripting](https://github.com/marrow/marrow.script), [cli](http://packages.python.org/pyCLI/), [argparse](http://docs.python.org/library/argparse.html)

Additional interesting packages
* [mimeparse](http://code.google.com/p/mimeparse/) for parsing Content-Type and Accept headers
* [rauth](https://github.com/litl/rauth), a Python library for OAuth 1.0/a, 2.0, and Ofly.
* [requests](https://github.com/kennethreitz/requests), Python HTTP Requests for Humans.
* [GeoAlchemy](http://www.geoalchemy.org/), GIS Support for SQLAlchemy.

A good list of possibly acceptable packages can by found on the [Python wiki](http://wiki.python.org/moin/WebComponents).
Good candidate micro packages could also be found in the 
[Werkzeug](http://werkzeug.pocoo.org/docs/),
[Marrow](https://github.com/marrow/) and
[repoze](http://docs.repoze.org/) projects.


Zen of &#181;
========
* Modular is better than monolythic
* [Two](http://www.sqlalchemy.org/) [packages](http://jinja.pocoo.org/docs/) chasing one rabbit each do better than [one package](https://www.djangoproject.com/) chasing two rabbits
* [Clean, intuitive source code](http://backbonejs.org/docs/backbone.html) is better than documentation
* But [documentation](http://readthedocs.org/) is still essential
* Size matters, but not at the expense of clean, intuitive source code
* [Duck typing](http://en.wikipedia.org/wiki/Duck_typing) is good (_If it walks like a duck and it quacks like a duck, it probably is a duck_),
* [Duck punching](http://www.ericdelabar.com/2008/05/metaprogramming-javascript.html) is bad (_If it doesn't, punch it until it does_)


Component acceptability guidelines
==================================

For a package to be deemed micro
* it **must** have a very clearly defined scope of functionality and **must not** overstep it
* it **must** have an atomic scope of functionality, at some reasonable level of detail
* it **should** have proper documentation
* it **should** have a relatively small and very clean codebase, so as to be easily understandable
* it **must not** monkey patch another module, ever

Micropy.com future wishlist
===========================

Index of micro packages and tools
* category of package (based on role it takes on in an app)
* equivalent packages
* related packages (e.g. different backends, adaptors)
* related URLs (homepage, pypi, docs, github/bitbucket, google group, mailing list, external articles)
* related micropy.com articles

Articles
* guides and HOWTOs related to packages in the index
* DIY micro-frameworks: guides to combining micro packages
* package comparisons: comparing equivalent packages in terms of usability, performance, docs, etc.

Social Q&A à la Reddit/HN

Benchmarking
* standardized real-world apps (e.g.
  HN clone,
  to-do app with user accounts,
  web-based chat app with user accounts and rooms)
* app code must be on github/bitbucket
* standardized API for micro.py to talk to the deployed app and clients and collect the info
* e.g. test runs for 1h with 5 client machines generating requests,
  at the end micropy.com connects to them all, retrieves the information, compiles and displays it