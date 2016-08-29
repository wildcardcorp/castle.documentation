Language settings 
=================


.. image:: Language.png

.. .. code:: robotframework
   :class: hidden

   *** Test Cases ***

   Show Language setup screen
       Go to  ${PLONE_URL}/@@language-controlpanel
       Capture and crop page screenshot
       ...  ${CURDIR}/../../_robot/language-setup.png
       ...  css=#content

       Click link  autotoc-item-autotoc-1
       Capture and crop page screenshot
       ...  ${CURDIR}/../../_robot/language-negotiation.png
       ...  css=#content


.. .. figure:: ../../_robot/language-setup.png
   :align: center
   :alt: Language setup configuration

You can set up the default language for your site and the other languages it should be available in.

.. note::

   This is for the language of the *user interface* of Castle.
   It will **not** make the content you create be translatable.
   For that, you should enable the add-on "plone.app.multilingual" which is available in the :doc:`add-on section <add-ons>`


Should you have multiple languages, and plone.app.multilingual, enabled, you can set various options in the *Negotiation* tab:

.. image:: language2.png

.. .. figure:: ../../_robot/language-negotiation.png
   :align: center
   :alt: Language negotiation configuration

.. note::

    These are important choices, which are hard to change after you have made them, so think about them carefully when setting up multilingual sites.

