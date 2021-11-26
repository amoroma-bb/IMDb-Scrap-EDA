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
## Data Cleaning and validation
    1. replace certificate to num list
    2. fillna of Metascore and Gross with mean
    3. replace rating to 5 categories (> 9.5, 8.5 ~ 9.5, 7 ~ 8.5, 5 ~ 7, < 5)

## Normalization 
    - (x - miu)/range for each x in title, year, certificate, metascore, votes, gross, movie_time_min

## Simple machine learning model
    - LogisticRegression
    - Training Accurancy: 74.78 %
    - Testing Accurancy: 74.02 %

## Hyperparameter Tuning and Cross Validation
    - DecisionTreeClassifier
        CV result: 89.9 %
        params: max_depth=19, min_samples_split=10, random_state=17
    - SVC
        CV result: 90.6 %
        params: C=1000, gamma=1, random_state=17
    - RandomForestClassifier
        CV result: 97.1 %
        params: bootstrap=False, max_features=3, random_state=17
    - LogisticRegression
        CV result 75.2 %
        params: C=10.0, penalty='l1', random_state=17, solver='liblinear'
    - KNeighborsClassifier
        CV result: 95.6 %
        params: metric='manhattan', n_neighbors=19, weights='distance'
