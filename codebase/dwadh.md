Deployable Web Application Directory Hierarchy
=====

DWADH is a system of structuring web application repositories so as to make deployment
easier and self-contained. Its scope is not meant to be generic, although it can likely
be adapted to situations not originally intended for.

Features
--------
* Easy VCS-based deployment, particularly when combined with something like
  [git-flow](https://github.com/nvie/gitflow). No packaging is required, distributing
  the code for a deployment is just a matter of cloning the master branch of your repository.
* Self-contained deployments. All files related to the application are contained
  within the deployment directory, so regardless of where the system likes to keep
  log files, it'll always be easy to find the app's.
* All files are arranged into sensible directories inspired by the
  [Filesystem Hierarchy Standard](https://wiki.linuxfoundation.org/en/FHS). If you've ever
  used Linux before, you'll know where to find the logs.
* VCS-controlled dependencies. DWADH prescribes a directory dedicated to 3rd party
  source code. Although not necessary, these libraries can be managed via
  [git submodules](http://git-scm.com/book/en/Git-Tools-Submodules)
  (or [Mercurial subrepos](http://mercurial.selenic.com/wiki/Subrepository?action=show&redirect=Subrepositories)
  but these are considered problematic), making it possible to push
  back upstream any changes made in the course of developing your own code.

Typical setup
-------------
DWADH is not ideal for all situations. This is the setup it's aimed at:
* git repository, with git submodules in `./usr/src`
* Python application served by Nginx (with a backend preferably served over uwsgi or fcgi)
* virtualenv environment set up in `./`

Directory structure
-------------------
- `./bin` - executable scripts (shared with virtualenv's)
- `./etc` - configuration files. E.g. Paste Deploy ini files, Nginx configuration, HTTP\_AUTH user file, pip install list.
- `./src` - sources for the application. The Python code should be in its own package inside this
  directory. Other subdirectories can be created for different packages specific to this same app,
  or even for code in other languages, e.g. SQL.
- `./usr` - static files, unchanged during the normal running of the application
- `./usr/src` - 3rd party source code, preferably in the form of git submodules
- `./usr/share` - static files served directly by the web server
- `./usr/templates` - (optional) template files used by your application
- `./var` - variable files, likely to change during the normal running of the application
- `./var/log` - log files for e.g. nginx, paste, uwsgi or custom scripts you create
- `./var/run` - run-time files such as socket or pid files

usr vs. var
-----------
In the Linux LHS, the distinction between usr and var is useful because usr, being guaranteed to be static,
can be mounted read-only, for security or from read-only media. That isn't generally a concern for
web application deployment (although it could potentially be an interesting security approach). Instead,
the separation is useful in order to easily exclude from the VCS repository all variable data pertaining
only to the local deployment.

I can't hold all these templates
--------------------------------
Keeping template files under `./usr/templates` is a controversial choice.
Many people prefer to keep them inside their package source, but in certain
situations it makes more sense to have them "belong" to the deployment/repository rather than to the package.
