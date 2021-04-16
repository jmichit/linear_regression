# Predicting NFL career longevity from the Draft and Combine
John Michitsch

## Abstract

Can player success be accurately predicted using the NFL Draft and Combine information?
As America's favorite sport, many people love to watch the games, but the draft has become an event unto itself.
Fans of every team, especially the bad teams with the first picks, hope the GM / coaches / owners make the correct call and draft the next All-Pro... and avoid the next bust. 

## Design
Sports websites were researched to figure out what was available in this domain. 

## Data

### Data Sources
Data was obtained from the following websites:
nflcombineresults.com
sports-reference.com
pro-football-reference.com

### Data Acquired
Data was scraped from these websites to obtain:
1) The draft data for each year (draft pick, team, player name, etc.)
2) The combine data for each year (player name, forty yard dash, shuttle time, bench press reps, etc.)
3) Data from individual player pages to compile college statistics (games played, college name, conference, years played)
The data was collection from 1990 to 2010 - 5000+ records of 10+ fields using request library to obtain the html and BeatifulSoup to parse the page. An archiving scheme was employed to pickle the response object on page load and unpickle if found to minimize page hits as the code needed to be modified and rerun. 

## Algorithms

### Feature Engineering

1 - Many of the features are categorical - so dummying of these variables was needed before modeling
2 - Base model was serverely underfit - used PolynomialFeatures to explore freature interaction
3 - Explored and abandoned log transorms - did not appear to help improve the model in this case

### Models
Various Linear models provided in sklearn.lineau_model were evaluated to find the best modeling outcome. 
Linear model with one key feature ("draft pick") as the base, then compared iwth multi feature Linear Models, models with PolynomialFeatures and dummied categorical variables, as well as Lasso and Ridge models.

### Model Evaluation and Selection

Training dataset was split into train vs. test 80/20 split with 5 fold cross validation used for LinearRegression, LassoCV, and RidgeCV. 

LassoCV adn RidgeCV 

## Tools

Numpy and Pandas for data manipulation
Matplotlib / Seaborn for plotting
BeautifulSoup for HTML scraping, pickle for archiving html 
Scikit-learn packages modeling

## Communication

Findings are consolidated in a pdf presentation and the supporting Jupyter Notebooks can also be found here.
