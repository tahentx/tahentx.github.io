## MTA Madness!
#### April 3, 2020

This week, my colleagues and I were tasked with exploring NYC's MTA turnstyle data. Our mandate was to identify the best stations for a women's organization to do outreach. We supplemented the data with some demographic data, but the core of our efforts were on munging and tidying the dataset for analysis. It was all of our first experience doing real EDA. Data can be found [here] (http://web.mta.info/developers/turnstile.html).

One of the first challenges was deciding how to interpret the identifier informtion. In addition to the station names, there were also columns identifying "Control Area", "Remote Unit", and "Subunit Channel". Not being familiar with those fields in relation to the stations, it was not apparent whether this metadata would help us. 

The second challenge was the time interval between measurements. The cumulative ridership total was counted every four hours starting at midnight. It took some work to "group by" across stations for the same interval - and I thought 4 hours is too coarse a measure for such a high volume variable. 

There were certainly more obstacles. But I gained an appreciation for the less glamorous part of the work.

My contribution was to try to find headcount data for the big tech companies in the city and locate the offices in relation to the highest volume stations that we identified. Unfortunately, the data collection was manual, as you can tell from the hard-coded values in the code below.

```
stations = [
    '14th/Union Sq.',
    'Penn',
    'Grand Central',
    'Port Authority',
]

pct = [16,7,1,1]

sns.barplot(stations,pct)
plt.xlabel("Top Stations")
plt.ylabel("Headcount as % of Ridership")
plt.title("Headcount Near Top Stations")
plt.savefig(fname='tech')

```

