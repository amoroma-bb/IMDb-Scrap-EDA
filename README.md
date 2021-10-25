# Scrap IMDb with bs4 and requests
## 1. Find the URL for each genre

Genre: Action, Adventure, Animation, Biography, Comedy, Crime, Drama, Family, Fantasy, Film-Noir, History, Horror, Music, Musical, Mystery, Romance, Sci-Fi, Sport, Thriller, War, Western

## 2. To the each genre page scrap the information and scarp the next page

The information of a movie
- Rank
- Title
- Year * The year tag of 50. Rush is (Ⅰ)(2013), so we need use [-5:-1] to get the correct year
- Certificate *Some certificates' value are none
- Runtime
- Genre
- Rating
- Metascore *Some metascore' value are none
- Intro
- Votes
- Gross *Some gross' value are none
- URL

Get the next page URL

With openpyxl module to write the information into a sheet


## 3. Scrap Process
Scrap the genre list one to last
    Scrap the current page, get the next page url
    Write to Excel
        Scrap the next page
            To the end
* When rank over 999, it conclues colon ','

# Data Analysis
