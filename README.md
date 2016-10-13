# Umbraco Vorto Grid Rich Text Editor

An Umbraco plugin replacement for the Umbraco Grid TinyMCE Rich Text Editor to resolve the issue with TinyMCE not re-initialising when you swich languages in the wonderful Vorto plugin.

This is designed for the situation where you have Vorto wrapping the standard Umbraco Grid.

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