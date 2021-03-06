.. _render-template:

========================================
Choose an alternative rendering template
========================================

Sometimes you must render a plugin with a slightly different template, other than the given default.
A possible solution is to create a new plugin, inheriting from the given one and overriding
the ``render_template`` attribute with a customized template. This however adds another plugin to
the list of registered CMS plugins.

A simpler solution to solve this problem, is to allow a plugin to be rendered with a customized
template out of a set of alternatives.


Change the path for template lookups
====================================

Some Bootstrap Plugins are shipped with templates, which are optimized to be rendered by Angular-UI_
rather than the default jQuery. These alternative templates are located in the folder
``cascade/bootstrap3/angular-ui``. If your project uses AngularJS instead of jQuery, then configure
the lookup path in ``settings.py`` with

.. code-block:: python

	CMSPLUGIN_CASCADE = {
	    ...
	    'bootstrap3': {
	        ...
	        'template_basedir': 'angular-ui',
	    },
	}

This lookup path is applied only to the Plugin's field ``render_template`` prepared for it. Such a
template contains the placeholder ``{}``, which is expanded to the configured ``template_basedir``.

For instance, the **CarouselPlugin** defines its ``render_template`` such as:

.. code-block:: python

	class CarouselPlugin(BootstrapPluginBase):
	    ...
	    render_template = 'cascade/bootstrap3/{}/carousel.html'
	    ...

.. _Angular-UI: http://angular-ui.github.io/bootstrap/versioned-docs/0.13.4/


Configure Cascade Plugins to be rendered using alternative templates
====================================================================

All plugins which offer more than one rendering template, shall be added in the projects
``settings.py`` to the dictionary ``CMSPLUGIN_CASCADE['plugins_with_extra_render_templates']``.
Each item in this dictionary consists of a key, naming the plugin, and a value containing a list of
two-tuples. The first element of this two-tuple must be the templates filename, while the second
element shall contain an arbitrary name to identify that template.

Example:

.. code-block:: python

	CMSPLUGIN_CASCADE = {
	    ...
	    'plugins_with_extra_render_templates': {
	        'TextLinkPlugin': (
	            ('cascade/link/text-link.html', _("default")),
	            ('cascade/link/text-link-linebreak.html', _("with linebreak")),
	        )
	    },
	    ...
	}


Usage
-----

When editing a **djangoCMS** plugins with alternative rendering templates, the plugin editor
adds a select box containing choices for alternative rendering templates. Choose one other than the
default, and the plugin will be rendered using that template.
