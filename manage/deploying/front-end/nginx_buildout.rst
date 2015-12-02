Buildout and recipe
====================

If, and only if, you cannot use a platform install of nginx you may use the recipe and buildout example below to get started.

* http://www.martinaspeli.net/articles/an-uber-buildout-for-a-production-plone-server

* https://pypi.python.org/pypi/gocept.nginx

A buildout will download, install and configure nginx from scratch.
The buildout file contains an nginx configuration which can use template variables from ``buildout.cfg`` itself.

When you change the configuration of nginx in buildout you probably don't want to rerun the whole buildout, but only the nginx part of it::

    bin/buildout -c production.cfg install balancer

Config test
============

Assuming you have a buildout nginx section called ``balancer``::

    bin/balancer configtest

    Testing nginx configuration
    the configuration file /srv/plone/isleofback/parts/balancer/balancer.conf syntax is ok
    configuration file /srv/plone/isleofback/parts/balancer/balancer.conf test is successful

Deployment configuration
=========================

`gocept.nginx <https://pypi.python.org/pypi/gocept.nginx/>`_ supports a special deployment configuration where you manually configure all directories.
One important reason why you might wish to do this, is to change the location of the ``pid`` file.
Normally this file would be created in ``parts``, which is deleted and recreated when you re-run buildout.
This interferes with reliably restarting nginx, since the pid file may have been deleted since startup. In this case, you need to manually kill nginx to get things back on track.

Example deployment configuration in ``production.cfg``::

    # Define folder and file locations for nginx called "balancer"
    # If deployment= is set on gocept.nginx recipe it uses
    # data provider here
    [nginx]
    run-directory = ${buildout:directory}/var/nginx
    etc-directory = ${buildout:directory}/var/nginx
    log-directory = ${buildout:directory}/var/logs
    rc-directory = ${buildout:directory}/bin
    logrotate-directory =
    user =

    [balancer]
    recipe = gocept.nginx
    nginx = nginx-build
    deployment = nginx
    configuration =
            #user ${users:balancer};
            error_log ${buildout:directory}/var/log/balancer-error.log;
            worker_processes 1;

Install this part::

    bin/buildout -c production.cfg install balancer

Then you can use the following cycle to update the configuration::

    bin/balancer-nginx-balancer start
    # Update config in buildout
    nano production.cfg
    # This is non-destructive, because now our PID file is in var/nginx
    bin/buildout -c production.cfg install balancer
    # Looks like reload is not enough
    bin/nginx-balancer stop ; bin/nginx-balancer start


Manually killing nginx
=======================

You have lost ``PID`` file, or the recorded ``PID`` does not match the real ``PID`` any longer.  Use buildout's starter script as a search key:

.. code-block:: console

    (hardy_i386)isleofback@isleofback:~$ bin/balancer reload
    Reloading nginx
    cat: /srv/plone/isleofback/parts/balancer/balancer.pid: No such file or directory

    (hardy_i386)isleofback@isleofback:~$ ps -Af|grep -i balancer
    1001     14012     1  0 15:26 ?        00:00:00 nginx: master process /srv/plone/isleofback/parts/nginx-build/sbin/nginx -c /srv/plone/isleofback/parts/balancer/balancer.conf
    1001     16488 16458  0 16:34 pts/2    00:00:00 grep -i balancer
    (hardy_i386)isleofback@isleofback:~$ kill 14012

    # balancer is no longer running
    (hardy_i386)isleofback@isleofback:~$ ps -Af|grep -i balancer
    1001     16496 16458  0 16:34 pts/2    00:00:00 grep -i balancer

    (hardy_i386)isleofback@isleofback:~$ bin/balancer start
    Starting nginx

    # Now it is running again
    (hardy_i386)isleofback@isleofback:~$ ps -Af|grep -i balancer
    1001     16501     1  0 16:34 ?        00:00:00 nginx: master process /srv/plone/isleofback/parts/nginx-build/sbin/nginx -c /srv/plone/isleofback/parts/balancer/balancer.conf
    1001     16504 16458  0 16:34 pts/2    00:00:00 grep -i balancer

Debugging nginx
===============

Set nginx logging to debug mode::

    error_log ${buildout:directory}/var/log/balancer-error.log debug;

www-redirect
============

Below is an example how to do a basic *yourdomain.com -> www.yourdomain.com* redirect.

Put the following in your ``gocept.nginx`` configuration::

    http {
        ....
        server {
                listen ${hosts:balancer}:${ports:balancer};
                server_name ${hosts:main-alias};
                access_log off;
                rewrite ^(.*)$  $scheme://${hosts:main}$1 redirect;
        }

Hosts are configured in a separate buildout section::

        [hosts]
        # Hostnames for servers
        main = www.yoursite.com
        main-alias = yoursite.com

More info

* https://stackoverflow.com/questions/7947030/nginx-no-www-to-www-and-www-to-no-www