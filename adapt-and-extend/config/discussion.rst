Discussion
========== 

.. image:: Discussion.png

.. .. code:: robotframework
   :class: hidden

   *** Test Cases ***

   Show Discussion setup screen
       Go to  ${PLONE_URL}/@@discussion-controlpanel
       Capture and crop page screenshot
       ...  ${CURDIR}/../../_robot/discussion-setup.png
       ...  css=#content

.. .. figure:: ../../_robot/discussion-setup.png
   :align: center
   :alt: Discussion configuration


You can control all aspects of Castle's built-in Discussion module:

- do you want to enable comments at all?
- if yes, do you want to allow anonymous comments?
- do you want to moderate comments?

There are also various settings to protect your site from spam and malicious content.


For public sites, there are also add-ons available to integrate other comment solutions like Disqus, which have more robust spam protection.

But since these integrate external services, that is usually not acceptible on Intranets.
Then again, on an intranet, you will have far less trouble with anonymous and spammy commenting, and you may even trust the users there enough to allow posting links.

