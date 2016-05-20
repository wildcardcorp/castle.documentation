Introduction
=============

**What is z3c.form all about?**

HTML forms are the cornerstone of modern web applications. When you interact with Plone, you use forms all the time - to search the content store, to edit content items, to fill in your personal details. You will notice that most of these forms use the same layout and conventions, and that they all rely on common patterns such as server-side validation and different buttons resulting in different actions.

*z3c.form* is the current approach to programmatically create forms in Plone.
This library defines the standard form view base classes, as well the default widgets.
For reference see the *z3c.form* `documentation <http://docs.zope.org/z3c.form>`_.

The following documentation will show you how to create a form with *z3c.form*.
Tools and patterns of *z3c.form* that are consistent with those used for Dexterity development,
as shown in the :doc:`Dexterity developer manual </external/plone.app.dexterity/docs/index>`.
All of Dexterity’s standard add and edit forms are all based on *z3c.form*.

Over the years, several approaches have evolved to deal with forms. A few of the most important ones are:


-  Creating a simple view with an HTML form that submits to itself (or another view),
   where the request is validated and processed in custom Python code.
   This is very flexible and requires little learning,
   but can also be fairly cumbersome,
   and it is harder to maintain a common look and feel and behaviour across all forms.
   See the :doc:`Views and viewlets </develop/plone/views/index>` for some hints on one way to build such views.
-  Using the *CMFFormController* library.
   This relies on special page objects known as “controller page templates” that submit to “controller python scripts”.
   The form controller takes care of the flow between forms and actions,
   and can invoke validator scripts.
   This only superficially addresses the creation of standard form layouts and widgets, however.
   It is largely deprecated, although Plone still uses it internally in places.
-  Using *zope.formlib*. This is a library which ships with Zope.
   It is based on the principle that a *schema interface* defines a number of form fields,
   constraints and so on.
   Special views are then used to render these using a standard set of widgets.
   Formlib takes care of page flow,
   validation and the invocation of *actions* - methods that correspond to buttons on the form.
   Formlib is used for Plone’s control panels and portlets.
   However, it can be cumbersome to use,
   especially when it comes to creating custom widgets or more dynamic forms.
-  Using `z3c.form`_. The library is inspired by formlib,
   but more it is more flexible and modern.
   It is the current best practice to create forms in Plone.


Add-Ons to *z3c.form*
---------------------

A number of add-on modules to *z3c.form* library have been developed,
that simplify or enhance the integration experience.
They range from new field types and widgets, to extensions that add functionality to the forms.
We will make use of some of these add-ons in this tutorial.
The most important ones are:

-  `plone.z3cform`_ makes *z3c.form* usable in Zope 2.
   It also adds a number of features useful in Zope 2 applications,
   notably a mechanism to extend or modify the fields in forms on the fly.
-  `plone.app.z3cform`_ configures *z3c.form* to use Plone-looking templates by default,
   and adds few services, such as a widget to use Plone’s visual editor and “inline” on-the-fly validation of forms.
   This package must be installed for *z3c.form*-based forms to work in Plone.
-  `plone.autoform`_ improves *z3c.form*’s ability to create a form from a schema interface.
   By using the base classes in this package,
   schemata can be more self-describing, for example specifying a custom widget,
   or specifying relative field ordering.
   We will use *plone.autoform* in this tutorial to simplify form setup.

 .. note::

   The `plone.directives.form`_ add-on provided tools for registering forms using convention-over-configuration.
   In general Plone development has moved away from convention-over-configuration and embraces explicit with ZCML instead.
   Its not recommended to use `plone.directives.form`_ anymore.

.. _plone.z3cform: https://pypi.python.org/pypi/plone.z3cform
.. _plone.app.z3cform: https://pypi.python.org/pypi/plone.app.z3cform
.. _plone.autoform: https://pypi.python.org/pypi/plone.autoform
.. _plone.directives.form: https://pypi.python.org/pypi/plone.directives.form
.. _z3c.form: https://pypi.python.org/pypi/z3c.form
