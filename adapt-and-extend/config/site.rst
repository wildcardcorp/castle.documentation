Site Configuration 
==================


.. image:: sitesettings.png

.. .. code:: robotframework
   :class: hidden

   *** Test Cases ***

   Show Site setup screen
       Go to  ${PLONE_URL}/@@site-controlpanel
       Capture and crop page screenshot
       ...  ${CURDIR}/../../_robot/site-setup.png
       ...  css=#content

.. .. figure:: ../../_robot/site-setup.png
   :align: center
   :alt: Site setup configuration


These settings should be changed for every site.

Site title
    The name of your website
Site Logo
    Upload your site logo. For extensive customization, you will want to create a special theme that will include your logo, but for a quick change this is enough.
Expose Dublin Core metadata
    This option allows information per content item, like Description, Tags, Author and others, to be shown to and ranked by search engines. It can help improve your search ranking, provided you fill in those fields with correct information.
Expose sitemap.xml.gz
    Almost always a good idea on a public website. It will make life for search engines easier, meaning they can better index your content.
Javascript for web statistics support
    To gather information for web analytics like Piwik (an open-source self-hosted option) or Google Analytics you can paste the required snippet of code here. Be aware that this can have legal implications (so-called "cookie laws") in some countries.
robots.txt
    By convention, search engines look for a file called robots.txt to show them what they should index or not.