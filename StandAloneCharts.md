# Introduction #

With this plugin charts can be rendered stand alone by creating an xfusion file.


# Chart Configuration #

The process of rendering a chart starts with the load of 2 properties files and the load of request [parameters](SupportedParameters.md).

On the first request, the global properties are loaded, this properties are defined in the _fusionCharts.properties_ file in the plugin's root folder. For each request, if the request has configured the location of a .xFusion file all the properties included in the file are loaded, this properties are called local properties. Finally the properties sent in the request are loaded (instance properties).