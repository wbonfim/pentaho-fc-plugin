# Introduction #

Parameters are used to set the way that plugin works and also to describe and format the chart that will be rendered. The plugin has two types of parameters:

  * Special Parameters - This type of parameters requires special treatments like labels, width, heigh, ... They either set the way that the plugin works or are placed on specific places according to FusionCharts specification.

  * Regular Parameters - This type of parameters are just added to the chart object and thus only have to be known by FusionCharts. On the example below attributes: showLegend, palette, animation and formatNumberScale can be passed on the plugin even if not referenced on the list:

```xml

<chart showLegend="1" palette="2" animation="1" formatNumberScale="0" numberPrefix="$" pieSliceDepth="30" startingAngle="125">
<set label="Leverling" value="100524"/>


Unknown end tag for &lt;/chart&gt;


```
For more regular parameters check the FusionCharts documentation.


# List of parameters #

This list contains special parameters and the main regular parameters.

| **Name**  | **Key**  | **Data Type**  | **Is Mandatory**  | **Default**  | **Description**  | **Example**  | **Available Values**  |
|:----------|:---------|:---------------|:------------------|:-------------|:-----------------|:-------------|:----------------------|
| Data Access ID  | cdaDataAccessId | int()          | yes               | -            | define witch data access to be used in CDA file&nbsp;  | cdaDataAccessId=2;3 | -                     |
| Action (deprecated)  | action   | string         | no                | ""           | file of fusion plugin properties to use  | action: "PieChart3D.xfusion" | -                     |
| Solution (deprecated)  | solution  | string         | no                | ""           | solution where fusion plugin properties is  | solution: "bi-developers" | -                     |
| Path (deprecated)  | path     | string         | no                | ""           | path where fusion plugin properties is |  path: "fusion-charts/Fusion Charts Free"  | -                     |
| xFusionPath  | path     | string         | no                | ""           | path where fusion plugin properties is. replaces 3 properties above. |  xFusionPath  : "fusion-charts/Fusion Charts Free/file.xfusion"  | -                     |
| Chart Type | chartType | string         | yes               | -            | chart type       |              | see supported charts  |
| Width     | width    | int            | no                | ?            | chart width      | width=200    | -                     |
| Height    | height   | int            | no                | ?            | chart height     | height=200   | -                     |
| Render in Html5 | isHTML5  | string         | no                | -            | render chart in html5. When is undifined flash is used. | isHTML5=true | true or undefined     |
| Free Version  | free     | boolean        | no                | true         | Renders the chart for free (true) or not free version (false). | free=true    | -                     |
| CDA File Name  | cdaName  | String         | no                | -            | File Name of CDA  | cdaName=usa-quantity-ordered.cda | -                     |
| CDA File Solution  | cdaSolution  | String         | no                | 	solution parameter  | Solution of CDA File  | cdaSolution=fusionSolution | -                     |
| CDA File Path  | cdaPath  | String         | no                | path parameter  | Path of CDA file  | cdaPath=path  | -                     |
| CDA Parameters  | cdaParameters | String         | no                | ""           | Parameters to be passed to CDA  | cdaParameters=year;day | -                     |
| CDA ID Range Value | rangeValueCdaId | int ()         | no                | -            | Cda ID for the query that will get the color range values. When only one value is set the the range value will multiply with the value of targetValueCdaId query. If is set two values the first value will multiply with the second one.  | rangeValueCdaId=3;5 | -                     |
| CDA ID Target Value | targetValueCdaId | int            | no                | -            | Cda ID for the query that will get the target value  | targetValueCdaId=4 | -                     |
| CDA output index | outputIndexId| int[.md](.md)  | no                | -            | Cda output indexs   | outputIndexId=4 | -                     |
| Color Range  | colorRange | string()       | no                | -            | Array of color codes to use in color range. Used in charts with colorRange XML element (Ex. Gauge)   | colorRange=FF654F;FF654F;F6BD0F;8BBA00 | -                     |
| Display Value  | displayValue | string()       | no                | -            | Array of labels to use in color range. Used in charts with colorRange XML element (Ex. Gauge)   | displayValue=Poor;Good;Very Good | -                     |
| Dashboard Mode  | dashboard-mode | Boolean        | no                | true         | it's to render the chart into a dashboard  | dashboard-mode=true | -                     |
| parentYAxis | parentYAxis | string()       | no                | -            | parentYAxis to each serie  | parentYAxis=P;P;S |                       |
| seriesTypes | seriesTypes | string()       | no                | -            | This attribute defines what the particular data-set will be plotted as | seriesTypes=BAR;AREA | COLUMN, AREA or LINE  |
| SeriesName Name  | seriesName | string         | no                | -            | This attribute sets the name of the series if not defined use the name of the column of the meeasures | seriesName=Series1;Series2 |                       |
| Series Param Name  | seriesParam | string         | no                | -            | This attribute sets the name of the series parameter in&nbsp; Chart Link Template | seriesParam=series |                       |
| Color List for Series| seriesColor | string         | no                | -            | This attribute sets the color for each category acording to the serie index  ONLY on Single Series Charts | seriesColor = FF654F;FF654F;F6BD0F |                       |
| Categories Param Name  | categoriesParam | string         | no                | -            | This attribute sets the name of the category parameter in&nbsp; Chart Link Template | categoriesParam=categories |                       |
| Color List for Categories  | categoriesColor | string         | no                | -            | sets the color for each categorie acording to de category index. ONLY on Multi Series Charts | categoriesColor = FF654F;FF654F;F6BD0F |                       |
| Value Param Name  | valueParam | string         | no                | -            | This attribute sets the name of the parameter with value in&nbsp; Chart Link Template | valueParam=value |                       |
| Chart Link Template  | chartLink | string         | no                | -            | The chart link parameter to be called when the user clicks on the chart. | chartLink=JavaScript: drillFunction('{series}','{categories}','{value}') |                       |
| Chart XML Mode  | chartXML | boolean        | no                | false        | Defines when should be rendered only the chart xml &nbsp;  | chartXML=true |                       |
| Realtime Datastamp Column  | datastampColumn | string         | no                | -            |Defines which dataset column will be used to forward incremental update values back to CDA &nbsp;  | datastampColumn=lastMaxId |                       |
|Prevent Cross-site scripting (XSS) | preventXSS| boolean        | no                | false        | If set to true a regex is applied preventing the user from sending javascript code. If chart links and other javascript are met to be used they must be defined on server side parameters either through global settings or the xfusion file. Besides that chart properties are limited to characters and digits or single characters.  | preventXSS=true| true / false          |
|Regex that verifies XSS scripting | xssRegex | string         | no                | false        | This regex is applied to all input parameters that come from the request, if any of them does not match an exception is thrown and the execution stops. The regex is only used if preventXSS is set to true.  If no regex is defined a default is applied. | xssRegex=[\\w;]**|[\\w,]**|[\\w\\&\\[\\]\\.]_|[\\w**]**|[\\w\\-]**|[\\w/]**_|                       |