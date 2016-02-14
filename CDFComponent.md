# Summary #
The Fusion Chart Plugin provides CDF component that can be used like any other CDF component.

# How to use #
To use this component you have to create a CDF component with the following type: "FusionChartComponent".

When defining a chart in the context of a dashboard you can define the chart parameters in a .xFusion file (local properties) or define them in the metalayer (instance properties). This two ways of defining the chart parameters can be associated to the FusionChart component's by setting the _path_ property with the .xFusion file path and by setting the _chartDefinition_ property with the metalayer, respectively. You can see a chart definition bellow and find some examples in the following path _bi-developers/fusion-samples/Dashboards_.
The global properties file stored on the plugin's root folder is still loaded at the beginning as in a standalone chart.

## Example ##
```
    var msColumnChart = {
            name: "columnChart",
            solution: "bi-developers",
            path: "fusion-charts/Fusion Charts Free",
            action: "MSColumnChart3D.xfusion",
            executeAtStart: true,
            htmlObject: "msColumnChart",
            chartDefinition: MetaLayerCharts.msColumnChartDef,
            type: "XDashFusionChartComponent",
            postExecution: function(){
            }
        }

var MetaLayerFusionCharts={
        msColumnChartDef: {
                width: "400",
                height: "150",
                chartType: "MSColumn3D",
                cdaDataAccessId:"2"
	}
}
```