# Introduction #

This page describes the usage of the real time functionality of the fusion charts realtime charts.

# Supported Charts #

  * RealTimeLine
  * RealTimeArea
  * RealTimeColumn
  * RealTimeLineDY (Dual Y)

# Usage #

  * Declare the component like any other fusion chart (refer to [CDF FusionChartComponent](CDFComponent.md))
  * Make use of the fusion charts parameter "refreshInterval" (in seconds) to make the chart autorefresh

```
realTimeColumnChartDefinition: {
...
  refreshinterval: 5,
...
}
```

  * (Optional) Define a column of your dataset to become an incremental pinpoint value for the chart using the "datastampColumn" parameter, this will make the column value be forwarded by the chart in the subsequent calls to the plugin and CDA using the "dataStamp" parameter. (functionality described in fusion charts realtime [documentation](http://docs.fusioncharts.com/widgets/Contents/index.html?RealTime/RealTimeOverview.html))

```
realTimeColumnChartDefinition: {
...
  refreshinterval: 5,
  datastampColumn: "max_id",
...
}
```

> Also, make sure your CDA query accepts a parameter called "dataStamp" (this should not be declared in the CDF component parameters array, as it's forwarded automatically by the fusioncharts plugin).

```
...
<DataAccess id="1" connection="1" type="kettle" access="public" cache="false">
  <Name>get twitter result count</Name>
  <Query>output</Query>
  <Parameters>
    <Parameter name="dataStamp" type="String" default=""/>
    <Parameter name="searchQuery" type="String" default="portugal"/>
  </Parameters>
</DataAccess>
...
```

Now your charts should be refreshing automatically using the query you defined!



# Stand alone version #
When using fusion charts directly with the .xfusion file
Its required to add the property  webAppPath

Example:
```
 webAppPath=pentaho 
```