# Oakland Sideshows & Crimes

## My datasets
For this project I used two datasets, the Oakland Police Deparment (OPD) [sideshow summary](https://nextrequestdev.s3.amazonaws.com/oaklandca/22-7316/99EAA1E3C350C4FB.xlsx?response-content-disposition=attachment%3B%20filename%3D%22Sideshow%20Summary%202019%20-%2030Nov2022_Disp%20Calls.xlsx%22&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAW2Y7QEIAQAROH3WX%2F20230503%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20230503T071334Z&X-Amz-Expires=1000&X-Amz-SignedHeaders=host&X-Amz-Signature=7e78a2deefc2a78e69e9b86dab0965433405340cf5143979ef5ed8c5b3e7b8f9) from 2019 to 2022 provided by the OPD and the [Oakland Crime Watch Data](https://data.oaklandca.gov/) provided by the City of Oakland’s Open Data [Platform](https://data.oaklandca.gov/) from 2019 to 2022.

I was going to see how sideshows could be related to crimes in different parts of Oakland as the city has been [grappling with the issue for years](https://oaklandnorth.net/2023/04/18/oakland-sideshows-council-crackdown/). The data in both datasets were categorized by “police beat.” A police beat is the area that a police officer/unit is assigned to patrol.

I have two 5-tab maps to examine the issue.

The first one shows the number of sideshows in each Oakland police beat from 2019 to 2022 and a map for the number of all sideshows throughout 2019 to 2022.

The second map shows the number of crimes that could be considered more relevant to sideshows. There are 51 crime types in [the original dataset](https://docs.google.com/spreadsheets/d/1jQXQ_xcd5Hln31OIjg_pB3p0KmEcI0AfJx7fnDxb_Ko/edit?usp=sharing), but I defined four crimes based on those 51 crime types that you can see in the maps.


My [sideshow summary dataset](https://docs.google.com/spreadsheets/d/1s1PkapY1sFnBbris3Y1k7aVVWkAh70AZ/edit?usp=sharing&ouid=109047557314096833567&rtpof=true&sd=true) has data in years, but the crime watch dataset has the data in timestamps that need to be converted to years. 

![01 timestamp to year](https://user-images.githubusercontent.com/78078218/235860192-3d8dc86a-35ad-4d1b-bb84-c173d41e6101.png)

1: Freeze row 1

2: Change column B from timestamps to years, because we are going to use analyze our data based of years:

- Select column B, then Format> Number> 2008

Now we have our data in years.

![02 timestamp to year](https://user-images.githubusercontent.com/78078218/235860409-3279cb3c-9219-42c3-8ad3-93df5f32e67b.png)

Now, to have a map for each crime category that consists of the number of our selected crimes in each police beat throughout 2019 to 2022 we need a pivot table from the Insert tab. In the pivot table we add PoliceBeat under Rows our data in table that has two columns, beats and numbers of crimes in each beat. Then we add CrimeType under Values. Now we add CrimeType and DateTime under filter. Under Filters, we filter our data based CrimeType we need and select 2019, 2020, 2021 and 2022 as our DateTime filter.

![1m](https://user-images.githubusercontent.com/78078218/235867731-2f694291-02f9-4cd9-8ef2-44fddef9ed1e.JPG)


Now we should copy the values for the selected crime to have a dataset to visualize it in DataWrapper. For other crimes, we can duplicate our currrent file and change the CrimeType under Filters to have the other datasets.

After creating our datasets we go to [DataWrapper](https://www.datawrapper.de/) to created out visualized maps.

From Menu go to Archive and create a folder for the first map and another one for the second map, this way it would be more organized.

From New select Map, then select Choropleth map. 

Choose your map. If the map that you need is not provided by Datawrapper, you should find or create your own map in .json or .geojson format. Datawrapper does not have Oakland maps, so I started searching for Oakland .json/.geojson map based police beats as my datasets were based on Oakland police beats. You may have to spend more time to find it becasue your map might be one websites which are not indexed on search engines.

You can edit any .json/.geojson file to have the map you need by using [MapShaper](https://mapshaper.org/). For example if you cannot find a map for Austria neighbors, you can easily find a .json/.geojson Europe map and edit it to have a .json/.geojson map for Austria and its neighbors. [More help](https://academy.datawrapper.de/article/145-how-to-upload-your-own-map).

For my maps, I needed an Oakland map based on the police beats. DataWrapper even did not have a general map of Oakland, so after a long search I found a police beats map of Oakland at the [UC Berkeley GEODATA](https://geodata.lib.berkeley.edu/catalog/ark28722-s71s46). YAY! GO BEARS!

![download](https://user-images.githubusercontent.com/78078218/235873765-46bd524f-06a8-4ca1-ad88-c53845b31134.jpeg)

Upload your map from your computer then click Proceed. Next, under *Add your data* from *Upload* upload you data for the crime that you are going to create a map from.

Your table cannot have red cells, if it does you should fix it. 

![red](https://user-images.githubusercontent.com/78078218/235876094-331bc14b-bdc2-430d-a06d-b03e6e955b9c.JPG)

The first solution, that most times works, is to select the right *Matching key* under *Match*. Here, from *Matching key* we need to select a key that corresponds with our beats which is Beat (01x, 02x...).

![no red](https://user-images.githubusercontent.com/78078218/235877710-f21df77f-dbd6-4770-a61a-7b619b0da5dc.JPG)

When we had no red cell we are ready to *Visualize*. Here we can work on visual features of our map and add annotations to our map for more context. Finally, we go to the last stage and publish our map. We should do the same for the other maps to have all of our five maps. We use *Visualization only* to create our tabs. Tabs are link to other maps. [Find more here.](https://academy.datawrapper.de/article/305-how-to-add-tabs-and-drop-downs)

Below is my first 5-tab map which shows the number of sideshows in each Oaklamd police beats based on years.

![sideshow summary](https://user-images.githubusercontent.com/78078218/235881080-d3776862-3e7d-4e6c-87c1-8be0efe3c3e8.JPG)

[Click here to see the sideshow summary interactive map](https://www.datawrapper.de/_/PYga3/) 

On the interactive map you can toggle between diffrent years to see the number of sideshows in different beats and years.

My second map is again a 5-tab map which shows the number of crimes throughout 2019 to 2022 that could be affected by sideshows in a neighborhood.

![crime map](https://user-images.githubusercontent.com/78078218/235882511-c1ea865d-a200-40b8-86fb-b3f1634baab2.JPG)

[Click here to see the crime watch interactive map](https://www.datawrapper.de/_/FA3lT/)

On the interactive map you can toggle between diffrent crimes to see their numbers in different beats throughout 2019 to 2022.


## Sources: 
District 5 Councilmember [Noel Gallo](https://www.oaklandca.gov/officials/noel-gallo) who has been pursuing to pass a Sideshow Spectator and Promoter Ordinance to curb sideshows in Oakland:
- Phone: 510-238-7005
- Email Address: [Ngallo@oaklandca.gov](Ngallo@oaklandca.gov)

Oakland Deputy Police Chief, [Darren Allison](https://www.oaklandca.gov/staff/darren-allison) as an official form the Oakland Police Department, the OPD have been supporting Gallo’s ordinance as they say police does not have tools to fight sideshows that are diverting policing resources
- Email Address: [dallison@oaklandca.gov](dallison@oaklandca.gov) 


