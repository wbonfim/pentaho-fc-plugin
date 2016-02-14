# Overview #

The following image shows an overview of the workflow executed by the component to render a chart:
<img src='http://imageshack.us/a/img585/5093/pchpworkflow.png' alt='Image Hosted by ImageShack.us' /><br />

# Workflow details #

## Load Properties ##
The process of rendering a chart using the Fusion Chant Pentaho Plugin starts with the load of two properties files and the load of request parameters. The parameters are managed by Properties Manager. For more information about parameters check [Supported Parameters](SupportedParameters.md).
The Properties Manager has one Global Properties Manager and two maps of properties. On the first request, the Global Properties Manager loads the global properties (called global properties) which are defined in the _fusionCharts.properties_ file in the plugin's root folder.
For each request, if the request parameters has the location of an xFusion file, the  Properties Manager loads all the properties included in the file (called local properties). Finally the properties sent in the request are loaded (called instance properties).

All properties have an override order:

  1. Global Properties - Are the base properties
  1. Local Properties  - Override Global Properties
  1. Instance Properties - Override Global Properties and Local Properties

## Obtain Data (CDA) ##
After all properties are loaded, it's time to invoke the CDA to get data. CDA is used to get data to all types of charts and widgets. Some times the plugin has to execute more than one query depending on the type of the chart. All the results from the different queries are stored on a map for next steps.

## Obtain Data From Request (JSON) ##
If the data is already available on the initial request no need to use to CDA. This step converts the JSON data into Pentaho Result sets that are used from now on to build the chart.


## Fusion Component Factory ##
Different types of charts require generating specific XML nodes. To make the design more modular a factory is used to obtain the correct Fusion Component class based on the chart type.

## Generate XML ##
Each class knows how to correctly handle the chart properties and data to generate a valid xml. The xml is the output of the plugin.

## Render Chart ##
The XML is the output of the plugin which is sent as a response to the browser. On the browser the javascript function _renderChart()_ is called from file _standaloneChartRender.js_ and the Fusion Chart is rendered.