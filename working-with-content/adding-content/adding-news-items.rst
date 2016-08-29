Adding News Items
====================== 


Castle web sites have a built-in system for publishing news items.

Use the **Add...** menu for a folder to add a news item:

..image:: Add.png

.. code:: robotframework
   :class: hidden

   *** Test Cases ***

   Show add new news-item menu
       Go to  ${PLONE_URL}

       Wait until element is visible
       ...  css=span.icon-plone-contentmenu-factories
       Click element  css=span.icon-plone-contentmenu-factories

       Wait until element is visible
       ...  css=#plone-contentmenu-factories li.plone-toolbar-submenu-header

       Mouse over  news-item
       Update element style  portal-footer  display  none

       Capture and crop page screenshot
       ...  ${CURDIR}/../../_robot/adding-news-items_add-menu.png
       ...  css=div.plone-toolbar-container
       ...  css=#plone-contentmenu-factories ul

.. figure:: ../../_robot/adding-news-items_add-menu.png
   :align: center
   :alt: add-new-news-item-menu.png

You will see the *Add News Item* panel:

..image:: AddNews.png

.. code:: robotframework
   :class: hidden

   *** Test Cases ***

   Show new news-item edit form
       Page should contain element  news-item
       Click link  news-item

       Wait until element is visible
       ...  css=#mceu_16-body

       Capture and crop page screenshot
       ...  ${CURDIR}/../../_robot/adding-news-items_add-form.png
       ...  css=#content

.. figure:: ../../_robot/adding-news-items_add-form.png
   :align: center
   :alt:
   
Fill in the **Title** field and Castle will fill in the ID and Url field.  This screen also shows the state of the page, whether it is published, unpublished, or pending approval for publication. Click the **Create and Edit** button.  You will then see your news item ready to be edited.

The standard tiles for title and description, along with a visual editor area for body text and image and image caption fields. You can be as creative as you want in the body text area, and you can use the insert image (upload image) function to add as much illustration as needed. The images you upload for the news item will be added to the folder in which you are adding the news item.

