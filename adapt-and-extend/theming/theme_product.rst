======================================
Create a Plone 5 theme product (addon)
======================================

Introduction
============

Creating a theme product with the Diazo inline editor is an easy way to start
and to test, but it is not a solid long term solution.

Even if ``plone.app.theming`` allows to import and export a Diazo theme as a ZIP
archive, it might be prefereable to manage your theme into an actual Plone
product.

One of the most obvious reason is it will allow you to override Plone elements
that are not accessible from the pure Diazo features (like overloading content
views templates, viewlets, configuration settings, etc.).

Create a product to handle your Diazo theme
===========================================

To create a Plone 5 theme skeleton, you will use mrbob's templates for Plone.

Install mr.bob and bobtemplates.plone
-------------------------------------

To install mr.bob you can do::

   $ pip install mr.bob

and to install the needed bobtemplates for Plone, do::

   $ pip install bobtemplates.plone

Create a Plone 5 theme product skeleton with mrbob::

   $ mrbob -O plonetheme.tango bobtemplates:plone_addon

It will ask you some question::

   --> What kind of package would you like to create? Choose between 'Basic', 'Dexterity', and 'Theme'. [Basic]: Theme

here choose Theme and fill out the rest of the questions as you like::

   --> Author's name [MrTango]:

   --> Author's email [md@derico.de]:

   --> Author's github username: MrTango

   --> Package description [An add-on for Plone]: Plone theme tango

   --> Plone version [4.3.6]: 5.0b3

   Generated file structure at /home/maik/develop/plone/plonetheme.tango

Now you have a new python package in your current folder::

   (mrbob)maik@planetmobile:~/develop/plone/plonetheme.tango
   $ ls
   bootstrap-buildout.py   buildout.cfg  CONTRIBUTORS.rst  MANIFEST.in  setup.py  travis.cfg
   bootstrap-buildout.pyc  CHANGES.rst   docs              README.rst   src


Bootstrap & buildout your development environment
-------------------------------------------------

You can run::

   $ python bootstrap-buildout.py
   Creating directory '/home/maik/develop/plone/plonetheme.tango/bin'.
   Creating directory '/home/maik/develop/plone/plonetheme.tango/parts'.
   Creating directory '/home/maik/develop/plone/plonetheme.tango/develop-eggs'.
   Generated script '/home/maik/develop/plone/plonetheme.tango/bin/buildout'.

Then you can run::

   $ ./bin/buildout

This will create the whole develoment environment for your package::

   $ ls bin/
   buildout                          code-analysis-hasattr               develop        pildriver.py
   code-analysis                     code-analysis-imports               flake8         pilfile.py
   code-analysis-clean-lines         code-analysis-jscs                  fullrelease    pilfont.py
   code-analysis-csslint             code-analysis-jshint                instance       pilprint.py
   code-analysis-debug-statements    code-analysis-pep3101               lasttagdiff    postrelease
   code-analysis-deprecated-aliases  code-analysis-prefer-single-quotes  lasttaglog     prerelease
   code-analysis-find-untranslated   code-analysis-utf8-header           longtest       release
   code-analysis-flake8              code-analysis-zptlint               pilconvert.py  test


Start your Plone instance and play with your theme product
----------------------------------------------------------

To start the plone instanc, run::

   $ ./bin/instance fg

The Plone instance will then run on http://localhost:8080.
Add a Plone site ``Plone``.
Then activate/install your theme product on http://localhost:8080/Plone/prefs_install_products_form.
The theme will be automatically enabled. If some think is wrong with the theme, you can always go to http://localhost:8080/Plone/@@theming-controlpanel and disable it. This control panel will never be themed, so it works regardless the theme might be broken.


Inspect your package source
---------------------------

Your package source code is in the src folder::

   $ tree src/plonetheme/tango/
   src/plonetheme/tango/
   ├── browser
   │   ├── configure.zcml
   │   ├── __init__.py
   │   ├── __init__.pyc
   │   ├── overrides
   │   └── static
   ├── configure.zcml
   ├── __init__.py
   ├── interfaces.py
   ├── locales
   │   ├── plonetheme.tango.pot
   │   └── update.sh
   ├── profiles
   │   ├── default
   │   │   ├── browserlayer.xml
   │   │   ├── metadata.xml
   │   │   ├── plonethemetango_default.txt
   │   │   └── theme.xml
   │   └── uninstall
   │       ├── browserlayer.xml
   │       ├── plonethemetango_uninstall.txt
   │       └── theme.xml
   ├── setuphandlers.py
   ├── testing.py
   ├── tests
   │   ├── __init__.py
   │   ├── __init__.pyc
   │   ├── robot
   │   │   └── test_example.robot
   │   ├── test_robot.py
   │   └── test_setup.py
   └── theme
       ├── index.html
       ├── manifest.cfg
       ├── rules.xml
       └── template-overrides

   11 directories, 25 files

As you see, the package contains already a Diazo theme::

   $ tree src/plonetheme/tango/theme/
   src/plonetheme/tango/theme/
   ├── index.html
   ├── manifest.cfg
   ├── rules.xml
   └── template-overrides

Here you can build your Diazo theme.


Build your Diazo based theme
============================

You can start with the example files in the theme folder, your own static html mockup or you use the Plone 5 default theme ``Barceloneta`` as a starting point.

Use your own static mockup
--------------------------

If you got a static mockup from your designer or from a website like http://startbootstrap.com where the example theme came from, you can use this without customization and just apply the Diazo rules on it. Another way is, to change the static mockup a little bit to use mostly the same css id's and classes. This way it is easier to reuse css/less from Barceloneta theme if you want.



Download and prepare a static theme
+++++++++++++++++++++++++++++++++++

Lets start with an untouched static theme like this bootstrap theme http://startbootstrap.com/template-overviews/business-casual/. Just download it and




Customizing Barceloneta Theme
-----------------------------

The easiest way is to customize the default Barceloneta theme.
To do so just download the Barceloneta theme as zip file from http://localhost:8080/Plone/++theme++barceloneta/@@download-zip and extract the content. Then pick the rules.xml and the index.html file and put it into your theme folder by replacing the existing files.

You can also pick the files directly from github: https://github.com/plone/plonetheme.barceloneta/tree/master/plonetheme/barceloneta/theme


Initial css and js resources
++++++++++++++++++++++++++++

Now create folders for your css and javascript resources and add the first files::

   $ tree .
   .
   ├── css
   │   ├── bundle.less
   │   └── main.less
   ├── index.html
   ├── js
   │   └── bundle.js
   ├── manifest.cfg
   ├── rules.xml
   └── template-overrides

The bundle.less file can look like this::

   /* bundle less file that will be compiled */

   // ### PLONE IMPORTS ###

   // //*// Font families
   @import "@{barcelonetaLessPath}fonts.plone.less";

   // //*// Core variables and mixins
   @import "@{barcelonetaLessPath}variables.plone.less";
   @import "@{barcelonetaLessPath}mixin.prefixes.plone.less";
   @import "@{barcelonetaLessPath}mixin.tabfocus.plone.less";
   @import "@{barcelonetaLessPath}mixin.images.plone.less";
   @import "@{barcelonetaLessPath}mixin.forms.plone.less";
   @import "@{barcelonetaLessPath}mixin.borderradius.plone.less";
   @import "@{barcelonetaLessPath}mixin.buttons.plone.less";
   @import "@{barcelonetaLessPath}mixin.clearfix.plone.less";
   @import "@{barcelonetaLessPath}mixin.gridframework.plone.less"; //grid Bootstrap
   @import "@{barcelonetaLessPath}mixin.grid.plone.less"; //grid Bootstrap


   // //*// Reset and dependencies
   @import "@{barcelonetaLessPath}normalize.plone.less";
   @import "@{barcelonetaLessPath}print.plone.less";

   // //*// Core CSS
   @import "@{barcelonetaLessPath}scaffolding.plone.less";
   @import "@{barcelonetaLessPath}type.plone.less";
   @import "@{barcelonetaLessPath}code.plone.less";
   //@import "deco.plone.less"; //uncomment for deco variant
   @import "@{barcelonetaLessPath}grid.plone.less"; //grid Bootstrap
   @import "@{barcelonetaLessPath}tables.plone.less";
   @import "@{barcelonetaLessPath}forms.plone.less";
   @import "@{barcelonetaLessPath}buttons.plone.less";
   @import "@{barcelonetaLessPath}states.plone.less";

   //*// Components
   @import "@{barcelonetaLessPath}breadcrumbs.plone.less";
   @import "@{barcelonetaLessPath}pagination.plone.less";
   @import "@{barcelonetaLessPath}formtabbing.plone.less"; //pattern
   @import "@{barcelonetaLessPath}views.plone.less";
   @import "@{barcelonetaLessPath}thumbs.plone.less";
   @import "@{barcelonetaLessPath}alerts.plone.less";
   @import "@{barcelonetaLessPath}portlets.plone.less";
   @import "@{barcelonetaLessPath}controlpanels.plone.less";
   @import "@{barcelonetaLessPath}tags.plone.less";
   @import "@{barcelonetaLessPath}contents.plone.less";

   //*// Patterns
   @import "@{barcelonetaLessPath}accessibility.plone.less";
   @import "@{barcelonetaLessPath}toc.plone.less";
   //@import "@{barcelonetaLessPath}backdrop.plone.less"; Still no implemented on Plone
   @import "@{barcelonetaLessPath}dropzone.plone.less";
   //@import "@{barcelonetaLessPath}formautofocus.plone.less"; Still no implemented on Plone
   @import "@{barcelonetaLessPath}modal.plone.less";
   @import "@{barcelonetaLessPath}pickadate.plone.less";
   @import "@{barcelonetaLessPath}sortable.plone.less";
   @import "@{barcelonetaLessPath}tablesorter.plone.less";
   @import "@{barcelonetaLessPath}tooltip.plone.less";
   @import "@{barcelonetaLessPath}tree.plone.less";

   //*// Structure
   @import "@{barcelonetaLessPath}header.plone.less";
   @import "@{barcelonetaLessPath}sitenav.plone.less";
   @import "@{barcelonetaLessPath}main.plone.less";
   @import "@{barcelonetaLessPath}footer.plone.less";
   @import "@{barcelonetaLessPath}loginform.plone.less";
   @import "@{barcelonetaLessPath}sitemap.plone.less";

   //*// Products
   @import "@{barcelonetaLessPath}event.plone.less";
   @import "@{barcelonetaLessPath}image.plone.less";
   @import "@{barcelonetaLessPath}news.plone.less";
   @import "@{barcelonetaLessPath}discussion.plone.less";
   @import "@{barcelonetaLessPath}search.plone.less";

   //@import "@{barcelonetaLessPath}barceloneta.plone.less";

   // ### END OF PLONE IMPORTS ###

   @import "main.less";

Here we import the specific parts of the default Plone 5 Barceloneta theme.
Feel free to comment out staff that you don't needed.

At the bottom you can see, that we import the main.less file.
The main.less will contain your custom styles and can look like this::

   h1 {
     color: green;
   }


More Diazo and plone.app.theming details
----------------------------------------

For more details how to build a Diazo based theme, look at :doc:`plone.app.theming</external/plone.app.theming/docs/index>` and :doc:`Diazo</external/diazo/docs/index>`.


Override Plone BrowserViews with jbot
=====================================

A large part of the Plone UI are provided by BrowserView or Viewlet templates.

That is the case for viewlets (all the blocks you can see when you call the url
``./@@manage-viewlets``).

.. note:: to override them from the ZMI, you can go to ``./portal_view_customizations``.

To overrides them from your theme product, the easiest way is to use
``z3c.jbot`` (Just a Bunch of Templates).

Since jbot is already included in the skeleton, you can just start using it, by putting in ``src/plonetheme/tango/browser/overrides/`` all the templates you want to override.
But you will need to name them by prefixing the template
name by its complete path to its original version.

For instance, to override ``colophon.pt`` from plone.app.layout, knowing this
template in a subfolder named ``viewlets``, you need to name it
``plone.app.layout.viewlets.colophon.pt``.

.. note:: ZMI > portal_view_customizations is an handy way to find the template path.

You can now restart Zope and re-install your product from the Plone control
panel (Site Setup > Add-ons).


