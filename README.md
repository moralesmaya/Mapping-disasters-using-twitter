# Mapping-disasters-using-twitter
part of a larger project which successfully captures live twitter data and maps it in real time. You can find the fiinal project on my Github under Projects. 


 A huge issue facing this project is that the large majority of tweets which are scraped are not accompanied by any location information. When you use tweepy to scrape twitter or any library for that matter, only  a very small portion of users have their location turned on and so you’ll get very few tweets with location data included.  We noticed that this small slice of the data is what past DSI projects used to map. We really wanted to improve upon this because we didn’t think it was great to map disaster tweets based on maybe 30% of your entire disaster data. To better access location data We came up with a plan to actually scrape each disaster tweet and pull out any city that was mentioned within the tweet.  

This ended up being a larger feat than we  initially thought,  a loop with only 100 tweets took hours to scrape over for location data because we’re simultaneously scraping over thousands of words in tweets and a place csv  and tthat initially had over 50,000 different  values. We cut this data frame down so it only included cities in the USA and Canada but even then we had over 8,000 cities to loop over and hundreds of words in tweets if we wanted to implement this function  in real time. 

It became clear that simple nested for loops and if in statements were not feasible. After countless hours of tinkering with this function we were able to combat  the lengthy duration of our function by using the try except loop you see in the screenshot on the left. Here we searched the dictionary of city names by key, then appended the tweet and the city name to a list. Initially this just appended the last value in the list over and over. To fix this we also had to append that initial list to another list, and then clear the first list with every iteration.  This  code did the same exact thing that our starter code did in hours in a matter of seconds. 
 


We then took what we had learned from our last function and built a similar  try except loop which you can see on the right. This loop  iterates over all of the values we appended to the location column, and pulls it’s respective coordinates from a dictionary I created earlier which simply contains USA and  Canadian cities and their coordinates 

So what we end up with is a list of all the latitude values and another list of all the longitude values  which we can plug directly into our mapping function. 

I used the code in the screenshot below to create a map of all the cities in which disaster tweets were occurring. Building upon this framework, my team and I were able to complete this function in real time, and provide updated maps as disasters occurred. 
