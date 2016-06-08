What's in a Web Name?
==========================

Individual content items on a Castle web site have discrete web addresses.
Castle creates these automatically based on the Title that you supply.

What's in a Web Name?
---------------------

The **Title** of content items, including folders, images, pages, etc., can be anything you want -- you can use any keyboard characters, including spaces.
**Titles** become part of web address for each item you create in Castle.
Web addresses, also known as URLs, are what you type in a web browser to go to a specific location in a web site (Or what you would click on to get there), such as:

www.mysite.com/about/personnel/sally/bio

OR

www.mysite.com/images/butterflies/skippers/long-tailed-skippers

Web addresses *do* have restrictions on allowed keyboard characters and spaces are not allowed.  Castle does a good job of keeping web addresses correct by using near-equivalents of the **Title** that you provide, by converting them to lowercase and substituting dashes for spaces and other punctuation.

To illustrate, let's take each of these two web addresses and split them out into their component parts:

::

    www.mysite.com/about/personnel/sally/bio
    ^
    website name
                   ^
                   a folder named About
                         ^
                         a folder named Personnel
                                   ^
                                   a folder named Sally
                                         ^
                                         a folder named Bio

In this example, Castle changed each folder title to lowercase, e.g., from Personnel to personnel.
You don't have to worry about this.
Castle handles the web addressing; you just type in whatever title you want.

And for the second example:

::

    www.mysite.com/images/butterflies/skippers/long-tailed-skippers
    ^
    website name
                   ^
                   a folder named Images
                          ^
                          a folder named Butterflies
                                      ^
                                      a folder named Skippers
                                               ^
                                               a folder named Long-Tailed Skippers

This example is similar to the first illustrating how there is a lowercase conversion from the title of each folder to the corresponding part of the web address.
Note the case of the folder named Long-tailed Skippers, Castle kept the dash, as that is allowed in the title and part of the web address, but it changed the blank between the words Tailed and Skippers to a dash in the web address, along with the lowercase conversion.

The web address of a given item is referred to as the **short name** in Castle.
When you use the **Rename** function you willl see the short name along with the title.

What’s in a Title?
------------------

The title of a content item not only affects the **short name** that is used in the URL, it is also displayed, with a twist, in the `title bar <http://en.wikipedia.org/wiki/Window_decoration#Title_bar>`_ of the browser window or in the browser tab.  The twist is that what is displayed consists of the *item title* and the *site title*, separated by an `Em dash <http://en.wikipedia.org/wiki/Dash#Em_dash>`_.
The site title is set in the *site control panel* (``http://yoursite.com/@@site-controlpanel``), but for the purposes of this section it is not necessary to have the permissions to access it.

For example, the title for the item at https://www.cia.gov/about-cia shows in the browser tab or title bar as:

*About CIA — Central Intelligence Agency*.

The part to the left of the Em dash, **About CIA** is the *item title*, while the part to the right, **Central Intelligence Agency**, is the *site title*.
The site title is appended to the item title with an Em dash automatically.  Technically, this is  what the ``<title>`` HTML element is set to.

Why is this important?  In and of itself, this behavior of a Castle site might often be overlooked.  However, it becomes important when looking at the results provided by a search engine such as Google.  When Google lists a page from a Castle site the title used is the same one just described (*item title — site title*).

Often you might want the homepage of your site to be listed in Google search results with just the site title.  However you can not leave the homepage item title empty, so how would you achieve this?  Thankfully, there is an easy solution:  make the homepage title **exactly identical** to the site title.

In the CIA example above if the homepage title were set to *Central Intelligence Agency*, then Google would list it simply as:

*Central Intelligence Agency*
