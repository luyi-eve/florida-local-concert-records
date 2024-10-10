# Tampa Bay’s most common concert acts: Here’s what the data show

- This is a data-driven music story that looked into a full decadde of performances data to see who plays the most in Tampa Bay area.
- Read the full story [here](https://luyi-eve.github.io/fl-abortion-costs/) 🎵🎸🎹 and find me at [here](https://www.tampabay.com/author/eve-lu/) 🐝✨.

## Data Collection

### 🎵 Setlist.fm - create fundamental dataset
I used [Setlist.fm's API](https://api.setlist.fm/docs/1.0/index.html) to retrieve local concert data across Florida by city, covering the years 2014 through 2024, with the dataset current up until August 2024, when the analysis was finalized. However, since Setlist.fm does not provide genre classification for its artists, I had to turn to the Spotify API to get genre information for the data retrieved from Setlist.fm.

### 🎵 Spotify API - add on genre classification

In order to obtain the genre data, I used the <b>Spotify Web API</b> for further exploration. The process involved three main steps, outlined below with reference links: <b>Step 1:</b> [Get Spotify Client credentials](https://developer.spotify.com/documentation/web-api/concepts/apps); <b>Step 2:</b> [Request an access token through Client Credentials Flow](https://developer.spotify.com/documentation/web-api/tutorials/client-credentials-flow); <b>Step 3:</b> [Make requests to Spotify Web API](https://developer.spotify.com/documentation/web-api/concepts/api-calls)

To prevent discrepancies between the artist names from Spotify and the original Setlist.fm data, I added two columns: "Original_Artist" and "Spotify_Artist" for comparison. This helped identify why unique artist names became non-unique after fetching data from the Spotify API. A common issue is that similar artist names, like "Fear Factory" and "Fear," were both matched to "Fear Factory" in Spotify's database, leading to duplicates. To address this, I manually verifIed those duplicates by cleaning data where "Original_Artist" and "Spotify_Artist" don't match. I also built up a pipline to exclude artists incorrectly assigned genres due to Spotify misidentifying them, which can happen when a tribute or cover band shares a name with a famous song or band.

### 🎵 Billboard Top 100


## Skills and Tools
