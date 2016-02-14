# Tutorial #
[Video with tutorial](http://www.youtube.com/watch?v=VPSaPm5-rgs)

# Installation - Since Pentaho 5.0 #
| Only available since version 2.2 of the plugin. |
|:------------------------------------------------|
| Version 3.0.0 Requires CDA 5.0.1 or higher to be installed on Pentaho Server |

  1. Stop Pentaho Server
  1. Depending on the version of Pentaho is necessary to add an import Handler:
    1. Pentaho 5.0: Change the file _system/importExport.xml_ to allow xFusion files. The requires adding xfusion in 3 places:
```
<util:map id="convertersMap"> 
   ... 
   <entry key="xfusion" value-ref="streamConverter"/> 
   <entry key="wcdf" value-ref="streamConverter"/> 
   <entry key="cdfde" value-ref="streamConverter"/>     
</util:map>

<bean id="NameBaseMimeResolver" class="org.pentaho.platform.plugin.services.importer.NameBaseMimeResolver"> 
   <constructor-arg>
      <map> 
          ... 
	<entry key="xfusion" value="text/plain"/> 
	<entry key="wcdf" value="text/plain"/> 
	<entry key="cdfde" value="text/plain"/> 
      </map>
   </constructor-arg>
</bean>

<util:list id="approvedExtensionList">
   ...
   <value>.xfusion</value>    
   <value>.wcdf</value>
   <value>.cdfde</value> 
</util:list>
```
    1. Pentaho 5.1: Change the file _system/ImportHandlerMimeTypeDefinitions.xml_ to allow xFusion files. Add this handler at the bottom of file:
```
<ImportHandler class="org.pentaho.platform.plugin.services.importer.RepositoryFileImportFileHandler">
	<MimeTypeDefinitions>
		<MimeTypeDefinition mimeType="text/plain" hidden="false" converter="streamConverter">
			<extension>xfusion</extension>
		</MimeTypeDefinition>
	</MimeTypeDefinitions>
</ImportHandler>
```
> > > Change the file _system/importExport.xml_ adding xfusion in 1 places:
```
<bean id="DefaultExportHandler" class="org.pentaho.platform.plugin.services.importexport.DefaultExportHandler">
	<property name="repository" ref="unifiedRepository" />
	<property name="localeExportList">
		<list>
			...
			<value>.xfusion</value>
		</list>
	</property>
</bean>
```
  1. Install FusionCharts plugin through Pentaho's marketplace
  1. Install dependencies
  1. Start Pentaho Server

## Installing FusionCharts XT (licensed) ##
  1. Extract the zip files provided by FusionCharts Team
    1. If your are installing a package you need to these steps for every file provided (charts, widgets, maps, ...)
  1. Look for the directory where the _`*`.swf_ files are
  1. Copy the _`*`.swf_ files to the plugin directory _fusioncharts/charts_
  1. Look for the directory JSClass where the _`*`.js_ files are
  1. Copy the directory contents to the plugin directory _fusioncharts/JSClass_

## CDE Components ##
  1. Extract the fusion\_pentaho-CDE zip file into the _pentaho-solutions/system/pentaho-cdf-dd_ path.
  1. Restart Pentaho Server

## Samples ##

To install the samples on the Pentaho User Console all you need to do is:
  1. Open Pentaho User Console (PUC)
  1. Go to the browse perspective
  1. Inside the public folder create a folder plugin-samples, if it doesn't exist already.
  1. Click on upload and select the fusionsamples zip file.
  1. A folder fusion-charts is created containing all the samples

#### (Deprecated) Installation - Pentaho 4.8 ####
Only possible until version 2.1 of the plugin.

  1. Extract the fusion plugin zip file into the _pentaho-solutions/system_ path.
  1. Extract the fusion samples zip file into the _pentaho-solutions/bi-developers_ path.
  1. Set _bi-developers_ folder to visible
    1. Edit file index.xml and set `<visible>true</visible>`
  1. Change the file _system/pentaho.xml_ to include another entry on the acl-files list: _`<acl-files>...,xfusion</acl-files>`_
  1. Restart Pentaho Server
  1. Open the Pentaho User Console (PUC) and refresh the solution repository.
  1. Restart Pentaho Server

# Usage #

## Standalone Chart ##

When defining a standalone chart you must create a .xFusion file where the parameters can be configured. You can find some examples in the following path _bi-developers/fusion-samples/Fusion Charts Free_. For more information check [StandAloneCharts](StandAloneCharts.md).

| If the licensed version is being used don't forget to set the _free_ parameter to "false". |
|:-------------------------------------------------------------------------------------------|

## Building CDF Dashboards ##

The plugin can easily be used on a CDF dashboard. To allow a seamless integration with, the plugin ships with a new CDF component called FusionChartComponent. This component works the exact same way as the existing chart components. The component can be found on the samples directory: _fusion-samples/Dashboards/FCPluginCDFComponent.js_. A sample dashboard can be found at the samples directory _bi-developers/fusion-samples/Dashboards_. For more information go to [FusionChartComponent here](CDFComponent.md).


## Enterprise Dashboards ##

You can simply drag and drop your xfusion file into the dashboard designer and create simple and effective dashboards. To test this feature you can simply go through the following steps:

Create a new dashboard in the PUC.
Navigate to the bi-developers/fusion-samples/Fusion Charts Free directory in the solution explorer.
Drag and drop the chart samples into the dashboard.

## Pentaho Analysis Visualizations ##
The plugin can be used to extend visualization types on Analyzer. For more information check this [page](IntegrationAnalyzer.md)


# Additional Information #
## Free Vs. Licensed Version ##
In the Free version the flash object use the `<embed>` tag and the element is  displayed above all other elements. In the Licensed Version the flash object use the `<object>` tag and you can define the displayed order

## XActions (Not Available) ##

The FusionCharts plugin is not available on Xactions. The chart library relies on Flash\html5 technologies requiring a browser for rendering.