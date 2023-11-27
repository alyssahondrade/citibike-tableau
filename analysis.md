# Analysis

## Introduction
### Membership
There are 4 options for the Citi Bike program: Single Ride, Day Pass, Citi Bike, Lyft Pink. The image below describes the pricing and inclusions of each option.

|![Citi Bike Pricing](https://github.com/alyssahondrade/citibike-tableau/blob/main/images/Citi%20Bike%20Pricing.png)|
|:---:|
|Citi Bike Pricing|

For the purpose of this analysis:
- Lyft Pink is disregarded.
- Citi Bike is defined as "member".
- Single Ride and Day Pass is combined as "casual".

### Validity
There are 3 categories of "validity" for this analysis.
1. "Short" trips are those which started and ended in the same station, with a trip duration of less than 1 minute. It can be assumed these trips are due to reattempting bike docking, potentially due to dock station faults, lack of user experience, or users changing their minds about using the program.

2. "Long" trips are the outliers of trips which have exceeded the included time in the fee. This is different per membership type:
	- 30 minutes for "Casual"
	- 45 minutes for "Member"

3. "Valid" trips are those which fall into neither category.

## Map
1. The 'City Official Map' is the city official requested map, which provides an overview of all the stations for the current and previous month.

|![NYC Boroughs](https://github.com/alyssahondrade/citibike-tableau/blob/main/images/NYC-boroughs.png)|
|:---:|
|New York City Boroughs|

This map provides observations regarding program usage in New York City boroughs:
- High usage in Manhattan and Brooklyn (particularly the NW area).
- Some usage in Queens and Bronx.
- No usage in Staten Island (potentially due to lack of stations in this area).

The general pattern is a high concentration in the Manhattan area, dispersing in a radial fashion - the further from Manhattan, the less engagement in the Citibike program.

2. The 'Context Map - Above the 90th Percentile' page of the story confirms the pattern described above. It demonstrates that stations with counts above the 90th percentile (approximately 5000 trips) are mostly in Manhattan.

The first phenomena explores the relationship between this fact as well as the trip validity (short, valid, long) and membership type (casual vs member).

3. There were trips that started and ended outside the New York City limits.

The second phenomena explores this, identifying the trends in the system boundary to determine whether more trips flow in or out of the New York City Limits

4. One station can have multiple latitude and longitude combinations. The workflow simplified this by taking an average for all stations, so that there is one set of coordinates (latitude, longitude) per station.


## Context
The popularity of start and end stations are explored, to provide context in the phenomena discovered. Understanding station popularity allows an appreciation of the trends discussed later on.

1. Over Sep-Oct period, there were three stations which were remained the top in terms of both Start and End Station popularity:
	- W 21 St & 6 Ave
	- West St & Chambers St
	- Broadway & W 58 St

For all three stations, for both months, more trips had these stations as the destination than origin. This is evident in the 'Top Stations Comparison' page of the story.

2. All Top 10 Stations (both Start and End) had usage between 8,000 and 15,000 trips per station. Assuming a 30-day month, for each of these stations, this would equate to approximately 250 to 500 trips per day.

This is a key observation to make, to fully appreciate the breakdown of valid trips in the first phenomena.

3. Due to the centrality of station concentration in Manhattan, it is reasonable to observe that all Top 10 Stations (both Start and End) are all within that borough.


## Phenomena 1 - Trip Validity and Membership
The map in the 'Phenomena #1 - Trip Validity and Membership' can be toggled to display "short trips" and "long trips" to further explore this phenomena.

1. The first table on the right, 'Trip Validity vs Membership' denotes the breakdown over the Sep-Oct period.

For "valid" trips:
- In September, 97.3% of the trips were valid for both "casual" and "member".
- In October, there were more valid "member" trips (97.7%) compared to "member" trips (97.4%). This could be attributed to the "member" types experience and minimal "long" trip percentage (0.2% for both months).

For "short" trips, there are more occurrences amongst "member" types (2.3% average) compared to "casual" (1.4% average). This could be attributed to the fact that there is no cost for "member" types when undocking a bike, whereas "casual" types pay $4.49 each time. This means they could be more willing to undock and dock a bike within a short period.

For "long" trips, "casual" types have more occurrences compared to "member" types, over both months. This could be attributed to lack of user experience, such as:
- Lack of familiarity with the overtime costs.
- Incorrect docking.

2. The second table on the right, 'Cost of Invalid Trips' denotes the breakdown of the number of trips and cost to the customer.
- It is logical that the cost per invalid trip for "short" trips for "casual" types cost $4, since the cost to undock is $4.49. This has cost users a collective $91,066 over the two-month period, simply by undocking and docking a bike without using the bike at all. This could have an impact on user satisfaction and program publicity, for example, causing unnecessary frustration when using the program for the first time.
- In terms of "long" trips, "casual" types have paid an average of $53, totalling to $967,493 of overtime fees, whilst "member" types have paid an average of $68, totalling to $771,560 of overtime fees.
- It is interesting to note that there were less "long" trips for "casual" types (approximately 28,000) compared to "member" types (approximately 85,000), despite 
- It is interesting to note that there were more "long" trips for "casual" types (approximately 18,000) compared to "member" types (approximately 11,000), despite "member" types accruing twice the average trip duration when they do go over time.

3. In terms of the map in this dashboard:
- More "short" trips occur in the Bronx (North of Manhattan), with "Brook Ave & E 138 St" Station accruing the most occurrences over Sep-Oct period. These Top 5 Stations with Short Trips should be investigated, whether there are faulty docks causing users to dock-undock.
- More "long" trips occur at Brooklyn and Queens, further away from the station usage epicentre of Manhattan. This is logical as users may need to ride to Manhattan, resulting in longer trips otherwise.

## Phenomena 2 - Trips Outside NYC
The map in the 'Phenomena #2 - Trips Outside NYC" demonstrates the stations which fall outside the New York City jurisdiction.

1. The panel on the right demonstrates there were 76 stations  used, whether as a start or end station, located outside New York City.

2. The bar charts on the bottom all demonstrate the flow of bikes in and out of the city. Overall, there has been a net flow of bikes out of the city. This is demonstrated by the much larger count for "End Stations" rather than "Start Stations".

These are key insights, as there needs to be a consideration for the number of bikes required to service the New York City jurisdiction itself. Users should not be discouraged from using the program in conjunction with neighbouring cities which also have stations. However, this metric must be tracked to ensure there are enough bikes available.
