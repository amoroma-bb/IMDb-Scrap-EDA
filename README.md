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

## 1. Data Cleaning and validation
- replace Certificate, Gross, Metascore ' ' with np.nan
- reset runtime to int
- reset the genre to split type column with 1 and 0

## 2. EDA
### The distribution of each certification of these movies dataset 
- R ranks the first, which is over 7000 movies
- PG-13 and PG ranks the second and third position 
    
- The distribution of rating 
    - most rating ranges from 6.1 to 8.1
    
- The distribution of movie time

- Year vs. Gross with hue of certificate

- Mean rating vs. Year
    - Mean rating decreases with the year increases

    - Mean movie time vs. Year

- Top_6 popular genre movie: Drama, Comedy, Action, Adventure, Crime, Thriller
    - Rating vs. Year
    - Movie time vs. Year
    - Gross vs. Year
    - Certificate counts 
    - dist plot
    
- Correlation 


# Machine Learning 