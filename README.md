# data-visualization

Hypothesis:
"There is a relation between the number of daylight hours and mental state"

To measure the mental state of the people I calculated the number of calls related to mental health that where done by day. I found this data in /data/raw and I used the EMS_Incident_Dispatch_Data.tsv.gz. Here I was able to find the date of the call and the type of the call(code that explains the reason of the call). From there I filtered the information to only take into consideration the ones related to mental health. 

Codes that reflect mental health:
- JUMPUP: someone threating to jump
- JUMPDN: someone that jumped
- EDP: psychiatric patient
- MCI42: civil disturbance
- MCI42P: civil disturbance
- ALTMEN: altered mental status

I order to relate the calls to the number of daylight hours I used the date. The length of each date I obtained it by scraping the data from different tables I found on a webpage that had a lot of details like sunrise... but I only took into consideration the field that had explicitly the length of the day (all of them had a range between 9 and 15 hours of light approximately)

After having that I created python file that counted the number of calls related to mental health that were done per day.

Then I created and awk file in order to put together the length of the day and how many calls were done on that day. After it, I created a file that used spark in order to reduce the information (round the decimals of the length so they are only or .5 or .0 to make easier the visualization) and take the average of the number of calls when the length of the day was x hours. 

Ex: if one day that had 9.5 hours of light, received 300 calls and other day that had 9.5 hours of light, received 350 calls, then this file combines them and say in other words. “The average of calls that were done when the day lasted 9.5 hours is 325 calls.”

After having this file I created a python file that creates a list with the possible lengths of a day that received calls (x coordinate) and created another list with the average of calls received on each day with x length (y coordinate). Then I used matplotlib in order to create a bars graph. This graph is saved in a pdf called graph.pdf

This graph didn’t show the inverse relation I was expecting with my hypothesis (I was expecting to see more calls done when having less hours of light). Even though it doesn’t show that, in the graph is possible to see a minimal direct relation (more calls when more hours of light). It is not possible to know if this is a real correlation if it was by chance.

It is possible that there is no relationship between mental health and daylight hours. However I still believe that there is a relation and maybe I didn’t choose the correct data in order to prove this hypothesis.


