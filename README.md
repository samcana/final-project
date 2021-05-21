
## Final Project, IronHack Data Analytics Bootcamp
May 2021

## Content

- [Project Outline](#project-outline)
- [Data & Cleaning](#data--cleaning)
- [EDA](#EDA)
- [The Function](#the-function)
- [Logistic Regression & Clustering](#logistic-regression--clustering)
- [Next Steps](#next-steps)
- [Links](#links)

## Project Outline

I started with a simple question: can we use a Python script to make recipe suggestions based on the ingredients available to a user, and the amount of time they have? Python returns a random recipe based on the user input ([more below](https://github.com/samcana/final-project/edit/main/README.md#the-function))

As the results turned to be quite random, I decided to look again at the dataset and the associations that could be drawn within it. Are certain ingredients more typical to certain cuisines? Can we use Machine Learning to predict which cuisine a recipe belongs to, based on ingredients?

Are certain cuisine types 'closer' to each other, and can we use Clustering to calculate which cuisine types have more similarities, based on their ingredients?

![Recipe slide](https://github.com/samcana/final-project/blob/main/images/Recipe%20Picker%20-%20First%20Elevator%20Pitch.png?raw=true)

## Data & Cleaning

I chose to work with a pre-existing dataset of approximately [8,000 recipes from Kaggle](https://www.kaggle.com/sarthak71/food-recipes), in the hope that the data would be clean and easier to work with. It turns out I was not completely correct in that respect :). Dropping null values from the dataset was straightforward enough. Only 12 columns were lacking ingredients, whilst approximately 50 columns were lacking any value for 'cuisine'. These were the 2 most important columns to my analysis, and dropping less than 1% of total rows did not significantly change my dataset.

Inconsisent naming of ingredients had the potential to cause issues. Looking at the data, I noticed ingredients with multiple spellings (mainly singular and plural), i.e. 'chillies' and 'chilli', 'potatoes' and 'potato' etc. I chose a consistent naming pattern for ingredients and use Regex to replace the ones that did not match.

What turned out to be more of a challenge was the language used in the recipes. The dataset is from an Indian website, and upon closer inspection I realised that 1,207 recipes were written in another language (I think Hindi?). As the non-ASCII characters would likely cause chaos in my code and in any Clustering, I ended up dropping these recipes. But 1,207 rows out of 8,000 is quite significant.

![hindi](https://github.com/samcana/final-project/blob/main/images/hindi%20recipes.png?raw=true)

## EDA

Unsurprisingly as the data is from India, most of the recipes are Indian. Delicious! Confusingly the most common cuisine type is 'Indian', despite a lot of recipes being split into regions of India lower down.

![img](https://github.com/samcana/final-project/blob/main/images/cuisine%20dist%20with%20code.png?raw=true|width=200px)

The most mentioned ingredients throughout the recipes are salt, sunflower oil, garlic and turmeric powder. So always keep them in your cupboard.

![img](https://github.com/samcana/final-project/blob/main/images/Screenshot%202021-05-19%20at%2015.21.09.png?raw=true|width=200px)

I also looked at the most common ingredients in different types of cuisine. Again not a shock that for Italian food, olive oil (and extra virgin olive oil) are the most important. For South Indian cuisine, the most used ingredients are dal (a general term for all split pulses, I believe) and curry leaves.

![img](https://github.com/samcana/final-project/blob/main/images/common%20ingredients%20per%20cuisine.png?raw=true)

## The Function

The first iteration of the script took an input from the user with the name of an ingredient. It then used .str.contains on the ingredients column of the dataset, and returned a recipe that contained the inputted ingredient. The next iteration asked for a 2nd ingredient as well the amount of time that the user has available for cooking. Based on '&' and '<=' operators, the script returns a recipe that features the 2 inputted ingredients, and whose total prep/cooking time is equal to or less than the amount of time that the user inputted.

In its current standing, the script returns a random recipe. It would be good to add more consideration for the user's interests (i.e. showing recipes similar to what they have tried before, or which they are more likely to enjoy).

## Logistic Regression & Clustering

I decided to explore the data further and wanted to find out: are certain combinations of ingredients more typical to certain cuisines. Could a Machine Learning model predict what cuisine a recipe belongs to based off its ingredients?

After encoding the ingredients into a format that the algorithm could work with, I ran the Logistic Regression model from SK Learn. The result was a low 0.42. The 'noise' in the data may have gotten in the way of the model I suspect there are still issues with the cleaning (especially in the format of the ingredients). Plus, having so many similar types of cuisine (such as the regions of India) probably made predictions difficult

![log-reg](https://github.com/samcana/final-project/blob/main/images/logistic%20regression.png)

I moved on to Clustering, to see if similarities could be found between on the ingredients (or the strings that are found in each row of ingredients). I used DictVectorier to perform 'One Hot Encoding' on the strings found in the ingredients of the dataset.

I then tried to use Principal Component Analysis (PCA) to try and reduce the large number of dimensions in the dataset, but at the same time maintaining the most relevant correlations. Due to the sheer number of varied cuisines in the dataset, I focused on 10 of the most popular cuisines for comparison.

In the first iteration there are no hard and fast 'clusters', but we see some vague correlation between, for example 'Italian' and 'Continental', and 'Tamil Nadu' and 'South Indian':

![cluster](https://github.com/samcana/final-project/blob/main/images/Screenshot%202021-05-19%20at%2023.24.32.png)

Next I tried to use t-SNE - [t-Distributed Stochastic Neighbor Embedding](https://www.youtube.com/watch?v=NEaUSP4YerM) (some very complex maths that is beyond me...but I let Python deal with).

We can see that clusters are getting slightly more clear, but the results are still not amazing. I suspect this is down to the cleaning and similarity issues mentioned before.

![tsne](https://github.com/samcana/final-project/blob/main/images/t-sne.png)

There is some amount of overlap visible between Tamil Nadu, Karnataka, and Kerala (as well as 'South India'). Looking at a map, those regions are close together in Southern India. It would make sense that their cuisines share similarities due to the ingredients typical in those regions.

![india](https://github.com/samcana/final-project/blob/main/images/Screenshot%202021-05-20%20at%2020.58.50.png?raw=true)

## Next Steps

For future iterations I would like to go back over the cleaning steps with the data (or even opt for a larger, more reliable dataset). Mainly to ensure consistency in the ingredients, and more variety in the cuisine types. Once clusters of recipes are more accurately defined, the ambition would be to have a recipe recommender that suggests a recipe based on its cluster (and also the dietary needs/preferences of the user)


## Links

[Presentation Slides](https://docs.google.com/presentation/d/16T8eqd4FB_QdyFFPViui57_d7QNLwv7HQO5QZsVXfp8/edit?usp=sharing)

[Notebooks](https://github.com/samcana/final-project/tree/main/notebooks)

[Tableau](https://public.tableau.com/views/Recipes_Final_Project/AvgNoIngredientsTimeTaken?:language=en&:display_count=y&publish=yes&:origin=viz_share_link)

