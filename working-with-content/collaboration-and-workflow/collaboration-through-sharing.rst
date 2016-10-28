Collaboration through Sharing
==================================


The Sharing item on the Toolbar empowers you to collaborate with other users through the use of several built-in roles.

Here a user has created a Folder called "Welcome to Castle" and has clicked on the "Sharing" option.

.. image:: sharing.png

.. .. code:: robotframework
      :class: hidden
 
   *** Test Cases ***

   Create sample content
       Go to  ${PLONE_URL}

       ${item} =  Create content  type=Folder
       ...  id=documentation  title=Documentation
       ...  description=Here you can find the documentation on our new product

   Show sharing menu

       Go to  ${PLONE_URL}/documentation

       Click link  css=#contentview-local_roles a

       Wait until element is visible
       ...  css=#user-group-sharing-container

       Update element style  portal-footer  display  none


      Capture and crop page screenshot
       ...  ${CURDIR}/../../_robot/sharing-menu.png
               ...  css=#content-header
               ...  css=div.plone-toolbar-container


.. .. figure:: ../../_robot/sharing-menu.png
      :align: center
      :alt: basic workflow menu



The default workflow for this Castle site has not been modified, so the folder is still "Private". Only she can see the contents.

Now she wants to let her colleagues add content to the folder.

Taking a closer look at the available permissions, they are:

-  **Can add** - When this permission is granted to a particular user (or group of users), that user can then add new content items.
   And since that user was also the creator of that content item, they will be able to edit it as they like.
-  **Can edit**- When this permission is granted on a folder, the user can not only edit the Folder (its title and description) but can also edit any of the items in the folder.
   Note, however, the user is not allowed to delete any of the content.
   When this permission is granted on a Page, for example, the user can only edit that Page and none of the other items in the folder.
-  **Can review** - When this permission is granted, the user can publish items.
-  **Can view** - When this permission is used on a folder or other item, the user can view the content but not make any changes.


.. note::

   Note: these permissions will override the default workflow permissions!
   For example, if you grant a user "Can view" permission on a Page that is in the Private state, that user will be able to see that Page.


Users and groups
----------------

Now, while it is handy to give one person the right permissions, it quickly becomes messy in a larger site.

Castle has a well-thought out system of :doc:`User and Group management</adapt-and-extend/config/users-groups>` that can help. For instance, if you put the people that work on the Sports section of your news site into the group "Sport editors", you can give them all the permissions they need at once.

And even more important, if Sally gets transferred from the Sports section to the Science section, you only have to remove her from one group, and add to another group, and all permissions on the whole site will work for her.


One final note: if the "Documentation" folder was not in the published state, and you had also not given your colleague the 'view' permission on the folder, but you had given that permission on a specific Page in this folder, he or she would have to know the exact URL to the Page to see it.

Permissions are very specific in Castle! In practice, it is usually clearer to give permission on a folder-by-folder base and not per document, as this becomes hard to maintain. Then again, if you need the permissions and the security to be this fine-grained, you can!



