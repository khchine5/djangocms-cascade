.. _introduction:

============
Introduction
============

**DjangoCMS-Cascade** is a collection of plugins for Django-CMS_ >=3.3 to add various HTML elements
from CSS frameworks, such as `Twitter Bootstrap`_ to the Django templatetag_ placeholder_. This
Django App makes it very easy to add other CSS frameworks, or to extend an existing collection with
additional elements.

**DjangoCMS-Cascade** allows web editors to layout their pages, without having to create different
`Django templates`_ for each layout modification. In most cases, one template with one single
placeholder is enough. The editor then can subdivide that placeholder into rows and columns, and
add additional DOM_ elements such as buttons, rulers, or even the Bootstrap Carousel. Some basic
understanding on how the DOM works is required though.

**Twitter Bootstrap** is a well documented CSS framework which gives web designers lots of
possibilities to add a consistent structure to their pages. This collection of `Django-CMS plugins`_
offers a subset of these predefined elements to web designers.


Extensibility
=============

This module requires one database table with one column to store all data in a JSON object. All
**DjangoCMS-Cascade** plugins share this same model, therefore they can be easily extended, because
new data structures are added to that JSON object without requiring a database migration.

Another three database tables are required for additional optional features.


Naming Conflicts
----------------

Some **djangoCMS** plugins may use the same name as plugins from **djangocms-cascade**. To prevent
confusion, since version 0.7.2, all Cascade plugins as prefixed with a Ϟ (koppa) symbol. This can
be deactivated or changed by setting ``CMSPLUGIN_CASCADE['plugin_prefix']`` to ``False`` or any
other symbol.


.. _Django-CMS: https://github.com/divio/django-cms/
.. _Twitter Bootstrap: http://getbootstrap.com/
.. _Django templates: https://docs.djangoproject.com/en/dev/topics/templates/
.. _templatetag: https://docs.djangoproject.com/en/dev/howto/custom-template-tags/
.. _placeholder: https://django-cms.readthedocs.org/en/latest/advanced/templatetags.html#placeholder
.. _DOM: http://www.w3.org/DOM/
.. _Django-CMS plugins: https://django-cms.readthedocs.org/en/latest/getting_started/plugin_reference.html
