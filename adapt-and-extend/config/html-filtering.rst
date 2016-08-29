=========================
Enabling HTML embed codes 
=========================

.. admonition:: Description

    You can set up Castle so it will not allow you to paste the code necessary to embed videos, slideshows or music players from popular websites such as Flickr, YouTube, Google Maps and MySpace. Learn how to adjust the HTML filtering to achieve the desired level of safety versus convenience.


.. image:: HTMLFiltering.png

.. .. code:: robotframework
   :class: hidden

   *** Test Cases ***

   Show HTML filter setup screen
       Go to  ${PLONE_URL}/@@filter-controlpanel
       Capture and crop page screenshot
       ...  ${CURDIR}/../../_robot/filter-setup.png
       ...  css=#content

.. .. figure:: ../../_robot/filter-setup.png
   :align: center
   :alt: HTML filter setup configuration


Important security note
------------------------

Making these configuration changes has serious security implications for your site.

Castle filters out many tags for a good reason:
they can be abused by your site users to create privilege escalation attacks.

If you have untrusted people allowed to create content on your Castle site, then a malicious person could create some "nasty" Javascript in some content, then trick a person with Admin rights into viewing that content.
That "nasty" Javascript can now do HTTP requests to interact with the Castle site with the full Admin rights granted to the trusted user.

*Bottom line: do not use this technique to enable embeddable content in your Castle site unless you are certain that you trust all users who are allowed to create content in your site.*


In Castle, there are two steps you need to take in order to embed content that is not using an *iframe* tag:

.. note::

   Per default, Castle will allow <iframe> as a valid tag.
   That enables embedding media from the most popular sites like Vimeo and YouTube.

   If you are in a high-security environment, simply add "iframe" to the list of *nasty tags* and embedding will stop working.


First, go to Site Setup>TinyMCE Visual Editor then click on the Toolbar tab.

- Enable the checkbox next to "Insert/edit Media"
- Scroll down to the bottom of the screen and click "Save"


Then, go to Site Setup>HTML Filtering

- Remove "Object" and "Embed" from the "Nasty Tags" list
- Remove "Object" and "Param" from the "Stripped Tags" list
- Add "Embed" to the "Custom Tags" list
- Scroll down to the bottom of the screen and click "Save"


With these changes made, you should be able to click newly-added "Embed Media" button in the TinyMCE toolbar.  You can paste in the URL of a YouTube video, and TinyMCE will do the rest for you!

For a Flickr slideshow, and most other embeds, switch into HTML editing mode and paste in the raw embed code.

.. note::

  To allow completely arbitrary HTML codes, see `David Glick's blogpost <http://glicksoftware.com/blog/disable-html-filtering>`_