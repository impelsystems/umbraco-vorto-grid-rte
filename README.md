# Umbraco Vorto Grid Rich Text Editor

An Umbraco plugin replacement for the Umbraco Grid TinyMCE Rich Text Editor to resolve the issue with TinyMCE not re-initialising when you swich languages in the wonderful Vorto plugin.

This is designed for the situation where you have Vorto wrapping the standard Umbraco Grid.

## How does it fix the issue?

In the loadTinyMce function within the grid angular directive link function, a call had been added to remove the tinymce editor before the tinymce.init call is made each time the directive is linked.

Other than that and giving the directive it's own name, it is a straight copy of the standard Umbraco Grid RTE directive. 

The tinymce remove call looks like:

`
try {
    tinymce.get(uniqueId).remove();
}
catch (ex) {}
`

The views/vorto.grid.rte.html file is included as a straight copy of the Umbraco Grid RTE view, however with the grid-rte directive changed to vorto-grid-rte to link in the modified directive.  

## Instructions

1. Clone this repo and copy the contents of /src into your App_Plugins folder under a subfolder of your choosing (I use ~/App_Plugins/VortoGridRte/)
2. Configure your Umbraco Grid config file ~/config/grid.editors.config.js file to use the plugin for the RTE, for example:

`
{
    "name": "Rich text editor",
    "alias": "rte",
    "view": "/App_Plugins/VortoGridRte/views/vorto.grid.rte.html",
    "render": "/Views/Partials/Grid/Editors/Rte.cshtml",
    "icon": "icon-article"
},
`