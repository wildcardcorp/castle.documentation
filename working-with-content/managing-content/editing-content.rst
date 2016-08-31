Editing Content
===============

Click "Edit" on the toolbar when you are viewing your page, and you will see the page with Tiles for editing the Title, Description, and Text of the page.  There will also be buttons on the top toolbar for **Properties** and **Layout**.

.. note::

    If you do wish to give a description, which is a generally a good idea, the description can be text only -- there is no opportunity for setting styling of text, such as bold, italics, or other formatting. This keeps the descriptions of Castle content items as simple as possible, and is also required by the :term:`Dublin Core` standard.

.. image:: EditPage.png

.. .. code:: robotframework
      :class: hidden

   *** Test Cases ***

   Edit folder
       Go to  ${PLONE_URL}
       Click element  css=#contentview-edit a
       Wait until element is visible
       ...  css=#mceu_16-body
       Capture and crop page screenshot
       ...  ${CURDIR}/../../_robot/edit-page.png
       ...  css=#content

.. .. figure:: ../../_robot/edit-page.png
      :align: center
      :alt: Editing a page

That's it. Change what you want, for instance changing the description or the content, and save.
The content item will be updated in Castle's storage system.
You can repeatedly edit content items, just as you can repeatedly edit files on your local computer.






