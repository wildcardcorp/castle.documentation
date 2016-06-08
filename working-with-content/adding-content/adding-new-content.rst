Adding New Content
==================


.. include:: ../../_robot.rst


A general overview of how to add new content items in Castle, including definitions of each standard content type.

New content items are added via the **Add . . .** pop up menu:

.. code:: robotframework
   :class: hidden

   *** Test Cases ***

   Show add new content menu
       Go to  ${PLONE_URL}

       Wait until element is visible
       ...  css=span.icon-plone-contentmenu-factories
       Click element  css=span.icon-plone-contentmenu-factories

       Wait until element is visible
       ...  css=#plone-contentmenu-factories li.plone-toolbar-submenu-header

       Mouse over  document
       Update element style  portal-footer  display  none

       Capture and crop page screenshot
       ...  ${CURDIR}/../../_robot/adding-content_add-menu.png
       ...  css=div.plone-toolbar-container
       ...  css=#plone-contentmenu-factories ul

.. figure:: ../../_robot/adding-content_add-menu.png
   :align: center
   :alt: add-new-menu.png

Adding content in Castle is done *placefully*, which means you should navigate to the section of your website where you want the new content to be placed **before** you use the **Add . . .** pop up menu.

You can of course cut, copy, and paste content items from one section to another if needed at any later time.

Content Types
-------------

In Castle, you can use a number of **Content Types** to post different kinds of content.
For example, to add a News Item you must use the **News Item** content type.
Below is a list of the available content types and what each are used for:

Page
    A Page in Castle is the basic content type.
    Use Pages to write the bulk of your web pages on your Castle website.
Link
    This is also referred to as the 'Link Object'. Do not confuse this with the links you create with the visual editor on pages or other content types.
    The Link content type is often used to include a link to an external website in Navigation and other specialized uses.
Event
    An Event is a content type specifically for posting information about an event (such as a fundraiser, meeting, barbecue, etc).
    This content type has a function which allows the site visitor to add the event to their desktop calendar. This includes applications such as: Google Calendar, Outlook, Sunbird and others.
Folder
    Folders work in Castle much like they do on your computer. You can use folders to organize your content and to give your Plone website a navigation structure.
News Item
    This content type is similar to a Page but News Item is specifically for posting news. You can also attach a thumbnail image to a News Item which then appears in folder summary views next to the summary of the News Item.


Title
-----

Nearly all content types in Castle have two fields in common: **Title** and **Summary**.

The **Title** of content items including folders, images, pages, etc., can be anything you want -- you can use any keyboard characters including spaces.
**Titles** become part of web address for each item you create in Castle.
Web addresses, also known as URLs, are what you type in a web browser to go to a specific location in a web site (Or what you would click on to get there) such as:

www.mysite.com/about/personnel/sally/bio

or

www.mysite.com/images/butterflies/skippers/long-tailed-skippers

Web addresses *do* have restrictions on allowed keyboard characters and spaces are not allowed. Castle does a good job of keeping web addresses correct by using near-equivalents of the **Title** that you provide by converting them to lowercase and substituting dashes for spaces and other punctuation.

The fields will vary according to the content type.  For instance, the Link content type has the URL field.  The File content type has the File field and so on.

Description
-----------

The **Summary** appears at the top of the page just under the Title.
Descriptions are often used to conjunction with a variety of Folder and Collection views (such as Standard and Summary).
The Description also appears in search results via Castle's native search engine.

The Description is just plain text without any form of mark-up. This is to keep it inline with the :term:`Dublin Core` standard, a long-established way of categorizing information.
