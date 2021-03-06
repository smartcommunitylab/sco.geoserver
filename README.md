# sco.geoserver
Extensions for GeoServer in order to integrate with the Open Services platform.


## Using Examples - OpenLayers

These examples show geospatial information from geoserver running on:

    geoserverUrl='http://localhost:8080/geoserver'
    
Prerequisites:

    1. start Geoserver with WPS extention enabled: mvn clean install -DskipTests -P wps
    
In examples/openlayers/config.js there are other url being used for integration with WSO2 AAC:

    Production Url:  wso2Url =   'http://192.168.43.202:8280'; 
    Api Url for accessing wms data: wmsUrl =    wso2Url+'/geoserverwmstest/1.0.0/wms2';
    Api Url for accessing wfs data: wfsUrl =    wso2Url+'/geoservertestwfs/1.0.0/wfs2';
    Api Url for accessing wcs data: wcsUrl =    wso2Url+'/geoservertest_wcs/1.0.0/wcs2';
    Api Url for accessing wps data: wpsUrl =    wso2Url+'/geoserver_wps/1.0.0/wps2';
    Api Url for executing post requests to wps: wpsUrlExecute =    wso2Url+'/geoserver_wps/1.0.0/execute';
    Authorization token: auth_token_wso2='Bearer '+'4f42ff1d-faf3-3d3b-9a07-efd001e38c5d';
    
    Name of the workspace: var workspace='topp';
    Name of the SLD: var sldName='play_ti';

## General Examples
 - The example no 1 shows the layer topp:states using WMS service. Since it uses ol.layer.Image type it treates the response as image tag, requesting the information without authorization headers - missing authorization token in the source of image tag.
 - The example no 2 shows the layer topp:states using WFS service. It uses Vector layer and deliver application/json data type. Extending XMLHttpRequest.prototype.send method we can set authorization token in headers and successfully retriving geogaphic information from WSO2 API Manager.
 - The example no 3 shows the layer topp:states using WCS service. Since it uses ol.layer.Tile type it treates the response providing images divided into a tile grid (missing authorization token in the source of image tag). Same prooblem as in example 1.
 - The example no 4 shows the layer topp:states using WMS service. It uses ol.layer.Vector type and deliver KML data type. Extending XMLHttpRequest.prototype.send method we can set authorization token in headers and successfully retriving geogaphic information from WSO2 API Manager.
 - The example no 5 shows the result of the WPS DescribeProcess Operation for the process gs:Aggregate.
 - The example no 6 shows the result of WPS Execute Operation. It counts the total number of states, sum all the number of persons, computes the average number of persons per state and give the maximum and minimum number of persons in a state.
 
 
## Scenario Examples

 - The example shows the set of the layers filtered by the tracking type.
 - It also uses the WPS HeatMap integrated inside the SLD (Style Layer Descriptor) in order to perform geospatial analysis for different purposes.
 - The content of this SLD can be find in this file : examples/openlayers/sldHeatmap.xml
 - We may also filter each of the layer depending on validity of tracking.
 - This demonstrates how CQL filters work by using the WMS CQL_FILTER  parameter to alter the data displayed by WMS requests.

## [OAUTH2 AAC plugin](https://github.com/smartcommunitylab/sco.geoserver/tree/master/aac.provider#)

This module allows GeoServer to authenticate against the OAuth2 Protocol .
In order to let the module work, it’s mandatory to setup and configure both oauth2 and oauth2-aac extension.
[The module](https://github.com/smartcommunitylab/sco.geoserver/tree/master/aac.provider#) is a sample extension for AAC OAuth2 Provider. 





