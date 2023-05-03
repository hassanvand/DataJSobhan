# Oakland Sideshows & Crimes

For this project I used two datasets, the Oakland Police Deparment (OPD) [sideshow summary](https://nextrequestdev.s3.amazonaws.com/oaklandca/22-7316/99EAA1E3C350C4FB.xlsx?response-content-disposition=attachment%3B%20filename%3D%22Sideshow%20Summary%202019%20-%2030Nov2022_Disp%20Calls.xlsx%22&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAW2Y7QEIAQAROH3WX%2F20230503%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20230503T071334Z&X-Amz-Expires=1000&X-Amz-SignedHeaders=host&X-Amz-Signature=7e78a2deefc2a78e69e9b86dab0965433405340cf5143979ef5ed8c5b3e7b8f9) from 2019 to 2022 provided by the OPD and the [Oakland Crime Watch Data](https://data.oaklandca.gov/) provided by the City of Oakland’s Open Data [Platform](https://data.oaklandca.gov/) from 2019 to 2022.

I was going to see how sideshows could be related to crimes in different parts of Oakland. The data in both datasets were categorized by “police beat.” A police beat is the area that a police officer/unit is assigned to patrol.

I have two 5-tab maps to examine the issue.

The first one shows the number of sideshows in each Oakland police beat from 2019 to 2022 and a map for the number of all sideshows throughout 2019 to 2022.

The second map shows the number of crimes that could be considered more relevant to sideshows. There are 51 crime types in the original dataset, but I defined four crimes based on those 51 crime types that you can see in the maps.


My sideshow summary dataset has data in years, but the crime watch dataset has the data in timestamps that need to be converted to years. 

![01 timestamp to year](https://user-images.githubusercontent.com/78078218/235860192-3d8dc86a-35ad-4d1b-bb84-c173d41e6101.png)

1: Freeze row 1

2: Change column B from timestamps to years, because we are going to use analyze our data based of years:

- Select column B, then Format> Number> 2008

Now we have our data in years.

![02 timestamp to year](https://user-images.githubusercontent.com/78078218/235860409-3279cb3c-9219-42c3-8ad3-93df5f32e67b.png)

Now To have a map for each crime category that consists of the number of our selected crimes in each police beat throughout 2019 to 2022 we need a pivot table from the Insert tab. In the pivot table we add PoliceBeat under Rows our data in table that has two columns, beats and numbers of crimes in each beat. Then we add CrimeType under Values. Now we add CrimeType and DateTime under filter. Under Filters, we filter our data based CrimeType we need and select 2019, 2020, 2021 and 2022 as our DateTime filter.

![1m](https://user-images.githubusercontent.com/78078218/235867731-2f694291-02f9-4cd9-8ef2-44fddef9ed1e.JPG)


Now we should copy the values for the selected crime to have a dataset to visualize it in DataWrapper. For other crimes, we can duplicate our currrent file and change the CrimeType under Filters to have the other datasets.

After creating our datasets we go to [DataWrapper](https://www.datawrapper.de/) to created out visualized maps.

From Menu go to Archive and create a folder for the first map and another one for the second map, this way it would be more organized.

From New select Map, then select Choropleth map. 

Choose your map. If the map that you need is not provided by Datawrapper, you should find or create your own map in .json or .geojson format. Datawrapper does not have Oakland maps, so I started searching for Oakland .json/.geojson map based police beats as my datasets were based on Oakland police beats. You may have to spend more time to find it becasue your map might be one websites which are not indexed on search engines.

You can edit any .json/.geojson file to have the map you need by using [MapShaper](https://mapshaper.org/). For example if you cannot find a map for Austria neighbors, you can easily find a .json/.geojson Europe map and edit it to have a .json/.geojson map for Austria and its neighbors. [More help](https://academy.datawrapper.de/article/145-how-to-upload-your-own-map).



