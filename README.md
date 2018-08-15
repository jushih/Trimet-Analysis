# Portland MAX Delay Analysis
This project examines Portland commuter rail (MAX) data with focus on weekday delays. The data is from the month of January 2018. As the trains run, they periodically transmit their location (latitude, longitude) and delay time which is positive if early and negative if delayed. Relevant data fields used in the analysis include:
* **tripID** - TripID the vehicle is servicing
* **vehicleID** - Identifies the vehicle
* **routeNumber** - Route number the vehicle is servicing
* **signMessageLong** - Vehicle's full over head sign displaying route name
* **lastStopSeq** - Stop sequence for the next stop this vehicle is scheduled to serve
* **delay** - Delay of the vehicle along its schedule recorded in seconds
* **timestamp** - Time this position was initially recorded

Below is a summary of findings and recommendations for Portland's rail system. The code used to generate the charts are in their respective Jupyter Notebooks.

### Delay Time Lapse
![Delay Time-Lapse](/images/hour.gif)  
Delays are concentrated during the morning rush hour and evening rush hour period.

### Distribution of Trimet Arrival Times
![Dist Plot](/images/dist_plot.png)

The data distribution shows most trains arrive on time or close to on time. More trains are delayed than early. Delay measurements cap out at -1000 seconds.

### Heatmap of Total Delay Count by Line
![Heatmap1](/images/count_hm.png)  
It's immediately apparent that not all trains run at all hours of the day. The Blue Gresham/Hillsboro Lines have remarkably more delays compared to other lines. Delays tend to concentrate around the waking hours of 6:00 - 21:00, there are fewer delays in the early AM hours. Evening rush hour has an impact on delays, with delays picking up around 16:00.

### Heatmap of Delay Frequency by Line
![Heatmap2](/images/norm_hm.png)  
After normalizing and looking at percent delayed, the Blue Gresham/Hillsboro Lines no longer stand out as most delayed - they simply run more often and thus has more total delays. Most lines show a greater percentage of delays during the evening hours, with delays visibly picking up around the 16:00 rush hour mark. Select lines such as MAX Yellow to Expo Center persistently run late throughout the day. The early AM hours and midday hours are least likely to be delayed.

### Heatmap of Average Arrival Time by Line
![Heatmap3](/images/avgarrival_hm.png)  
This chart includes early arrival data in the average. On average almost no trains arive earlier than scheduled, and most trains arrive close to on time with delays < 200 seconds. The AM hours (4:00) show the most on-time arrivals and evening hours show greater delays.

### Pareto Chart of Total Delay Time per Line
![Pareto](/images/delays-pareto.png)  
To make the most impact, Portland Trimet should focus on reducing delays in 4 routes: **MAX Blue Line to Hillsboro and Gresham**, **Max Yellow Line to Expo Center**, and **Max Red Line to Airport** which account for roughly **50% of all total delays**

### Ridership of Blue Line to Gresham
After finding the routes that are most commonly delayed, we can dig deeper into individual routes and their stops. I investigate the Gresham Blue Line ridership data to find that certain stops have a greater influx of riders getting on and off than others. Then I compare rider activity at each stop to the additional delay generated from stop to stop. 

![Ridership](/images/gresham_ridership.png)

![DelayByStop](/images/gresham_delay.png)

A notable stop is Gateway/NE 99th Ave Transit Center where there is the largest number of riders getting on and off and also the greatest increase in delay getting to the subsequent stop, E 102nd Ave. The delay could be attributed to the influx of rider activity. Another point of delay is between Providence Park and Oak SW 1st Ave stops, which crosses the heart of downtown. Note the data is missing some downtown stops that would be expected to show high ridership activity. But based on findings from available data, a second recommendation would be: **Portland Trimet should seek ways to alleviate or better faciliate rider traffic at bottleneck stops such as Gateway/NE 99th Ave Transit Center that is responsible for increasing delays.**


### Resources
https://developer.trimet.org/ws_docs/vehicle_locations_ws.shtml
https://github.com/Kennfucius/trimet
https://trimet.org/about/performance.htm
