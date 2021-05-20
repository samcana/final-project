
## Final Project at IronHack Data Analytics Bootcamp
May, 2021

## Content

- [Project Outline](#project-outline)
- [Data & Cleaning](#data--cleaning)
- [EDA](#EDA)
- [The Function](#the-function)
- [Clustering](#clustering)
- [Next Steps](#next-steps)
- [Links](#links)

## Project Outline

I started with a simple question: can we use a Python script to make recipe suggestions based on the ingredients available to a user, and the amount of time they have? Python returns a random recipe based on the user input ([more below](https://github.com/samcana/final-project/edit/main/README.md#the-function))

As the results turned to be quite random, I decided to look again at the dataset and the associations that could be drawn within it. Are certain ingredients more typical to certain cuisines? Are certain cuisine types 'closer' to each other, and can we use Clustering to calculate which cuisine types have more similarities, based on their ingredients?

![Recipe slide](https://github.com/samcana/final-project/blob/main/images/Recipe%20Picker%20-%20First%20Elevator%20Pitch.png?raw=true)

## Data & Cleaning

I chose to work with a pre-existing dataset of approximately [8,000 recipes from Kaggle](https://www.kaggle.com/sarthak71/food-recipes), in the hope that the data would be clean and easier to work with. It turns out I was not completely correct in that respect :). Dropping null values from the dataset was straightforward enough. Only 12 columns were lacking ingredients, whilst approximately 50 columns were lacking any value for 'cuisine'. These were the 2 most important columns to my analysis, and dropping less than 1% of total rows did not significantly change my dataset.

Inconsisent naming of ingredients had the potential to cause issues. Looking at the data, I noticed ingredients with multiple spellings (mainly singular and plural), i.e. 'chillies' and 'chilli', 'potatoes' and 'potato' etc. I chose a consistent naming pattern for ingredients and use Regex to replace the ones that did not match.

What turned out to be more of a challenge was the language used in the recipes. The dataset is from an Indian website, and upon closer inspection I realised that 1,207 recipes were written in another language (I think Hindi?). As the non-ASCII characters would likely cause chaos in my code and in any Clustering, I ended up dropping these recipes. But 1,207 rows out of 8,000 is quite significant.

![hindi](https://github.com/samcana/final-project/blob/main/images/hindi%20recipes.png?raw=true)

## EDA






ghg
g
h
gh
gh
gh
gh
gh
g
h


## The Function

(i.e. a recipe that features the 2 inputted ingredients, and whose total prep/cooking time is equal to or less than the amount of time that the 


gh
g
hg
h
gh
gh
gh
gh
g
hg



## Clustering
ghg
h
gh
g
g
hg
h
g
h

## Next Steps

fh
fgh
fgh
fgh
fg
hfg
hfg
h

## Links

