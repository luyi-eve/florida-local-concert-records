# Tampa Bay’s most common concert acts: Here’s what the data show

- Read the full story [here](https://www.tampabay.com/life-culture/music/2024/09/23/tampa-bay-st-petersburg-concerts-most/) 🎵🎸🎹
- For this story, I sifted through over 68,000 Florida concert records using setlist.fm and Spotify APIs, manually verified artist matches, and cross-referenced with Billboard Top 100 data for analysis, graphics, and reporting, pinpointing major artists performing in Tampa Bay.


## Data Collection & Cleaning

### 🎵 Setlist.fm - create basic master dataset
I used [Setlist.fm's API](https://api.setlist.fm/docs/1.0/index.html) to retrieve local concert data across Florida by city, covering the years 2014 through 2024, with the dataset current up until August 2024, when the analysis was finalized. However, since Setlist.fm does not provide genre classification for its artists, I had to turn to the Spotify API to get genre information for the data retrieved from Setlist.fm.

### 🎵 Spotify API - add on genre classification 

In order to obtain the genre data, I used the <b>Spotify Web API</b> for further exploration. The process involved three main steps, outlined below with reference links: <b>Step 1:</b> [Get Spotify Client credentials](https://developer.spotify.com/documentation/web-api/concepts/apps); <b>Step 2:</b> [Request an access token through Client Credentials Flow](https://developer.spotify.com/documentation/web-api/tutorials/client-credentials-flow); <b>Step 3:</b> [Make requests to Spotify Web API](https://developer.spotify.com/documentation/web-api/concepts/api-calls)

To prevent discrepancies between the artist names from Spotify and the original Setlist.fm data, I added two columns: "Original_Artist" and "Spotify_Artist" for comparison. This helped identify why unique artist names became non-unique after fetching data from the Spotify API. A common issue is that similar artist names, like "Fear Factory" and "Fear," were both matched to "Fear Factory" in Spotify's database, leading to duplicates. 

To address this, I manually verifIed those duplicates by cleaning data where "Original_Artist" and "Spotify_Artist" don't match. I also built up a pipline to exclude artists incorrectly assigned genres due to Spotify misidentifying them, which can happen when a tribute or cover band shares a name with a famous song or band. 

### 🗺️ OpenCage API - assign county to each city

Since Setlist.fm doesn't provide specific county data for each city, I used the OpenCage API to retrieve county information for each concert listed in the Setlist.fm data. <b>Note:</b> Some cities may not have been assigned a county by OpenCage. In those cases, I manually added the cities to the appropriate counties and updated the dataframe accordingly. To clarify, our concert data covers Hillsborough, Pinellas, and Pasco counties, which together make up the Tampa Bay region in this story.

### 🎵 Billboard Top 100 - retrieve annual Top 100 Billboard artists from 2014 to 2023

To retrieve data on the top 100 artists annually from Billboard's "[Year-end Charts Top Artists](https://www.billboard.com/charts/year-end/top-artists/)" for the years 2014 to 2023, I used the [billboard.py](https://github.com/guoguo12/billboard-charts?tab=readme-ov-file) to scrape the data.

For the final analysis, the complete master dataset that incorporates the Billboard data is referred to as "10_YEARS_MASTER_DATASET_MERGED_BILLBOARD(+2024).csv".

## Data Analysis

For the analysis, I delved into the questions outlined below, based on the dataset I have constructed:

- Which major artists have performed in Tampa Bay the most frequently?
- Which artists ranked in the top 100 have played the most shows in Florida without ever performing in Tampa Bay during that 10-year period?
- How does the percentage of rap shows in Tampa Bay compare to the rest of Florida?
- For each county, which musical genre has hosted the most concerts?
- In Tampa Bay, which genre has seen the most top-100 artist performances at each venue?
- In Tampa Bay, which were the highest-ranked artists at each of those venues each year?

Not all results are displayed or discussed in the story because not every show is recorded on setlist.fm. Therefore, some analyses based on the questions had to be excluded from the story.

## Data Source

- [Setlist.fm](https://www.setlist.fm)
- [Spotify](https://developer.spotify.com/documentation/web-api/concepts/api-calls)
- [Billboard Year-end Charts Top 100 Artists](https://www.billboard.com/charts/year-end/top-artists/)

## Come and Say Hiiii

- You can always find me [here](https://luyi-eve.github.io) 🐝✨ 
- Check out my other work with [Tampa Bay Times](https://www.tampabay.com/author/eve-lu/)🍀


