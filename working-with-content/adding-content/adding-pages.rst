Adding Pages
============ 


Pages in Castle vary greatly, but all are single "web pages," of one sort or
another.

To add a page, use the **Add...** menu for a folder:

.. image:: Add.png

.. .. code:: robotframework
      :class: hidden

   *** Test Cases ***

   Show add new page menu
       Go to  ${PLONE_URL}

       Wait until element is visible
       ...  css=span.icon-plone-contentmenu-factories
       Click element  css=span.icon-plone-contentmenu-factories

       Wait until element is visible
       ...  css=#plone-contentmenu-factories li.plone-toolbar-submenu-header

       Mouse over  document
       Update element style  portal-footer  display  none

       Capture and crop page screenshot
       ...  ${CURDIR}/../../_robot/adding-pages_add-menu.png
       ...  css=div.plone-toolbar-container
       ...  css=#plone-contentmenu-factories ul

.. .. figure:: ../../_robot/adding-pages_add-menu.png
      :align: center
      :alt: add-new-menu.png

Select **Page** from the menu, and you'll see the *Add Page* screen:

.. image:: AddPage.png

.. .. code:: robotframework
      :class: hidden

   *** Test Cases ***

   Show new page edit form
       Page should contain element  document
       Click link  document

       Wait until element is visible
       ...  css=#mceu_16-body

       Capture and crop page screenshot
       ...  ${CURDIR}/../../_robot/adding-pages_add-form.png
       ...  css=#content

.. .. figure:: ../../_robot/adding-pages_add-form.png
      :align: center
      :alt: Adding pages form
   
Fill in the **Title** field and Castle will fill in the ID and Url field.  This screen also shows the state of the page, whether it is published, unpublished, or pending approval for publication. Click the **Create and Edit** button.  You will then see your page ready to be edited.

The **Title** tile is at the top.

The middle tile is for the summary or description of this page.

**Text**, is where the action is for pages. The software used for making Pages in Castle, generically called *visual editor* and specifically a tool called TinyMCE, is a most important feature allowing you to do WYSIWYG editing.
WYSIWYG editing -- *What You See Is What You Get* -- describes how word processing software works.
When you make a change, such as setting a word to bold, you see the bold text immediately.

People are naturally comfortable with the WYSIWYG approach of typical word processors. We will describe later in this manual.

Markup languages
----------------

Your site-administrator may also enable markup languages.
If you are the sort of person who likes to enter text using mark-up formats, you may switch off the visual editor under your personal preferences, which will replace it with a simplified textentry panel.
The mark-up formats available in Castle are:

-   [Markdown](http://en.wikipedia.org/wiki/Markdown)
-   [Textile](http://en.wikipedia.org/wiki/Textile_%28markup_language%29)
-   [Structured Text](http://www.zope.org/Documentation/Articles/STX)
-   [Restructured Text](http://en.wikipedia.org/wiki/ReStructuredText)

Each of these works by the embedding of special formatting codes within text.
For example, with structured text formatting, surrounding a word or phrase by double asterisks will make that word or phrase bold, as in \*\*This text would be bold.\*\*
These mark-up formats are worth learning for speed of input if you do a lot of page creation, or if you are adept at such slightly more technical approaches to entering text.
Some people prefer such formats not just for speed itself, but for fluidity of expression.

