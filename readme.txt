=== In Series ===
Contributors: quandary
Donate link: http://remstate.com/donate/
Tags: links, navigation, post, posts, series
Requires at least: 1.5.2
Tested up to: 2.3.2
Stable tag: 3.1.0

Gives authors an easy way to connect posts together as a series.

== Description ==

In Series is a series management plugin. For readers, it provides several useful
links within series posts, such as tables of contents. Site administrators have
the ability to customize exactly which linking features are used, and where they
show up, *without* having to edit themes. Post authors get an easy interface for
adding, removing, and reordering posts in series -- independent of categories,
tags, and post dates.

In Series has the following major features:

* Link rendering
    * Tables of contents
    * First, previous, next, and last in series links
    * HTML document relation links (first, prev, next, last)
    * Lists of series
* Sidebar widgets
    * Table of contents (when viewing a post in a series)
    * Sorted list of series, with an optional length limit
        * Most recently posted to
        * Most recently created
        * Alphabetical
* Series manipulation
    * "In Series" control box in the post editing screen
        * Add a post to a new or existing series
        * Remove a post from a series it's in
        * Change the order of a post within a series
    * Comment mechanism for adding new posts to a new or existing series
    * Removing the last post from a series automatically deletes the series
* "Automatic" link insertion (no template editing required)
    * Easy-to-use basic configuration mode to handle most needs
    * Powerful advanced configuration mode for fine-grained control
    * Supports different layouts on single-post views vs. multi-post views
* Compatible with WordPress 1.5 through 2.3

== Installation ==

1. It is *highly* recommended that you back up your WordPress database.
1. Deactivate and delete any existing version of In Series you have installed
1. Unzip the In Series release file
1. Upload the in-series directory to your wp-content/plugins directory
1. Activate the plugin through the 'Plugins' menu in WordPress.
1. Alter the display formatting to your taste in the 'Series' sub-menu (under
'Options') in WordPress.
1. Create, modify, and delete posts as desired.

== Frequently Asked Questions ==

The FAQ list is maintained separately, so that it can be updated more frequently
than once each release.

[View the FAQ](http://remstate.com/projects/in-series/faq/ "Frequently Asked Questions about In Series")

== Screenshots ==

The screenshots are maintained separately, to vastly reduce the size of the file
you have to download, and so that new screenshots can be added more frequently
than once each release.

[View the screenshots](http://remstate.com/projects/in-series/screenshots/ "Screenshots of In Series")

== TODO ==

Need write ups for...

* The new widgets (ToC and Series List so far)
* "New" series -> existing on match

=== Configuring In Series ===

In Series configuration options are accessed through the 'Series' sub-tab under
the 'Options' tab in the WordPress administration interface. You must have the
'manage_options' capability (WordPress 2.0 and later) or have at least user
level 8 (prior to WordPress 2.0) to alter the In Series options. 

There are two configuration modes for In Series -- basic and advanced. Basic is
the default mode for new installations. Upgrades will default to basic mode only
if no layout changes have been made from the original defaults.

Note that basic and advanced modes are independent of one another. Changes made
in basic mode will not be reflected in the advanced settings, and vice-versa.
This means that if your upgrade defaults to advanced mode, you can safely switch
to basic mode and try it out. Switching modes will *immediately* apply the
configuration settings of the new mode.

== Basic Configuration ==

The basic configuration mode was created to improve ease of use, while
maintaining a reasonable level of formatting control, suitable for most blogs.
Configuration is done via the manipulation of check boxes and drop-down menus
within sentences.

= Table of Contents =

Unchecking the checkbox to the left of the "I want a ToC..." sentence will
completely disable the automatic rendering of tables of contents within posts
(it does not affect the ToC widget, if you have placed one in the sidebar).

If the checkbox is checked, then the tables of contents are rendered as the
sentence describes. The title may contain the special tokens %title and %series,
which expand (respectively) into the title of the post that the ToC is rendered
in, and the series that the ToC represents. When rendered "only in single-post
views", the table of contents will not show up unless the reader visits the
permalink to view the post by itself. Rendering at the top or bottom of the post
is mostly self-explanatory. Navigational links will always come before
(at the top) or after (at the bottom) of the table of contents, if both the
table of contents and navigational links are rendered on the same side.

= Navigational Links = 

Unchecking the checkbox to the left of the "I want navigational links..."
sentence will completely disable the automatic rendering of navigational links
within posts.

If the checkbox is checked, then navigational links will be rendered as the
sentence describes. The text used for the navigational links is described by the
"Links to the ... post in a series have the following text" sentences. These
text fields can contain the special tokens %title, %url, and %series which
expand (respectively) to the title of the target post, the URL of the target
post, and the name of the series that the target post belongs to. Rendering at
the top or bottom (or both) of the post is self-explanatory.

= Post Counts =

Unchecking the checkbox to the left of the "I would like post counts..."
sentence will prevent post counts from showing up in series lists.

If the checkbox is checked, then the number of posts present in a given series
will show up beside the series name in a series list (such as that rendered by
the widget). Rendering before or after the series name is self-explanatory.

= HTML Document-Level Links =

Unchecking the checkbox to the left of the "Use link tags..." sentence will
prevent document-level links from being generated.

If the checkbox is checked, document-level links for the first, previous, next
and last posts will be inserted into single-view post pages. If a page is the
first or last in its series, then the first/previous or next/last links are
omitted (respectively). The document-level links links will enable built-in
browser navigation and page prefetching for browsers that support these
features, and may improve web spiders' understanding of the series structure.

== Advanced Configuration ==

In order to provide maximum flexibility, In Series formats posts based on a set
of special formatting strings. The key component to all of these fields are a
set of special tokens. These are replaced with appropriate values, based on
context. The complete list of tokens is as follows:

* %content -- text of the post.
* %count -- the total number of posts in a series
* %entries -- complete list of recurring items, e.g., the entries in a table of
contents.
* %next -- link to the next post in the series (if one exists).
* %prev -- link to the previous post in the series (if one exists).
* %series -- title of the series.
* %title -- title of the post. Which post is based on context.
* %toc -- a table of contents enumerating all the published posts in a series.
* %url -- an unadorned URL. What this URL points to is based on context.

It is important to note that the above tokens may expand differently (or not at
all) if used inside of an HTML tag. A very common scenario that illustrates this
would be &lt;a href='%url' title='%title'&gt;%title&lt;/a&gt. The first %title will have
any HTML stripped out of it, and will have the remaining special characters
(like "'") escaped. The second %title, though, will not have any content
stripped or escaped. The special expansion rules apply as described in the list
below:

* Not expanded between &lt; and &gt;
    * %content
    * %entries
    * %next
    * %prev
    * %toc

* HTML-stripped and escaped between &lt; and &gt;
    * %count
    * %series
    * %title

* Expanded the same everywhere
    * %url

= Post Layout =

This option controls the manner in which each post is generated. It is important
to have the "%content" token (without the quotes) appear exactly once in this
field. More than once, and the post's contents will show up twice; if "%content"
isn't present at all, then your posts will not have any content. In Series will
not prevent you from making this mistake, so please double-check!

If you would like different layouts for single- vs. multi-page views, you can
can check the "Use a different layout..." checkbox, and use the "Post layout
(multi)" setting to define the layout to use in multi-page views. If you leave
the checkbox unchecked, then the layout specified by the "Post layout" field
will be used in all views.

Valid tokens for the post layout fields are:

* %content
* %next
* %prev
* %toc

= Next, Previous, First and Last Link =

These options control how the %next, %prev, %first and %last tokens are
expanded (respectively). The corresponding "on first" and "on last" post options
allow you to specify an alternate expansion on the first and last posts in a
series (i.e., when the link would be pointing to the page that the reader is
already on).

Valid tokens for these fields are:

* %series
* %title -- the title of the (next, previous, first, or last) post in the series
* %url -- a URL pointing to the (next, previous, first or last)  post in the
series

= Table of Contents Layout =

This option controls how the %toc token is expanded.

Valid tokens for this field are:

* %entries
* %series
* %title -- the title of the post that the Table of Contents is being generated
in

= Entry Link and Active Entry Link =

These fields control how the %entries token is expanded. The entry link field is
used for most of the entries. However, if the post that the %entry token would
ultimately be a part of is the same post that an entry would refer to, the
active entry link field is used instead. This allows you to prevent having a
table of contents with a link pointing to the page that you're already on (for
example).

These fields are present for both the table of contents, and the series list.

Valid tokens for these fields are:

* %count
* %series
* %title -- this value is changed for each entry in the list, representing the
title of each post that is part of the group (one at a time).
* %url -- this value is changed for each entry in the list, representing the
title of each post that is part of the group (one at a time).

= HTML Document-Level Links =

This option is exactly the same as the one in the basic configuration mode.

=== Manipulating Series ===

In Series tries to make it as easy as possible for authors to create and change
series. Series manipulation is handled with post editing; to change a post's
relationship with a series, start by editing the post.

== HTML Comment-Based Manipulation ==

You can use HTML comments to add a post to a series. This is useful if, for
example, you make a large number of blog posts via e-mail, or through an
interface other than the web interface. You can use the following comment tags
to control how In Series will treat a new post:

* &lt;!--Series-name: Your Series Name --&gt;
* &lt;!--Series-order: start --&gt;

The series name tag will control which series the post is added to. If the
series does not exist, it will be created. The series order tag will control
where in the series the post is placed. If no tag is present, In Series will
default to placing the post at the end of the series.

All In Series comment tags are removed after processing -- they do not appear
in the final post.

== Adding to a New Series ==

1. If you intend to save the post to have an author that is not the same as the
user you are logged in as, save the post first before making any series changes.
1. If the post is already in a series, you will need to remove it from that
series before you can add it to a new one (see Removing from a Series).
1. From the In Series sidebar, enter the name of the new series you wish to
create in the empty text box. Ensure that you have not already created a series
with the same name (In Series will not permit you to have two series with the
same name), and that the drop-down box is set to "--- New Series ---".
1. Save the post.

If you enter the name of a series that already exists, In Series will assume
that you wish to add the post to the already-existing series (as if you had
selected that series from the drop-down menu).

== Adding to an Existing Series ==

1. If you intend to save the post to have an author that is not the same as the
user you are logged in as, save the post first before making any series changes.
1. If the post is already in a series, you will need to remove it from that
series before you can add it to a new one (see Removing from a Series).
1. From the In Series sidebar, select the name of the series you wish to add the
post to from the drop-down menu.
1. Select the "start" radio button if you would like the post to be added as the
first post in the series; otherwise, leave the "end" radio button selected.
1. Save the post.

== Removing from a Series ==

Note that deleting a post will automatically remove it from any series that it
is in.

1. The In Series sidebar should contain the name of the series that the post is
a part of, followed by a drop-down menu. Select "--- Remove ---" from the
drop-down menu.
1. Save the post.

== Reorder in a Series ==

1. The In Series sidebar should contain the name of the series that the post is
a part of, followed by a drop-down menu. From that menu, select the name of the
post that you would like the current post to come *after*. If you would like the
post to be the first in the series, select "--- First ---".
1. Save the post.
