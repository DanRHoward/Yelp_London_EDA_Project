# Yelp_London_EDA_Project
Utilizing Yelp's API to gather data in the location of London and conduct EDA to gain business insight.

## Summary

### Summary

Regarding the basic statistics of our dataset, we gather that the following statements hold true (on average):

- A business will recieve **105** reviews,
- Aquire a rating score of just over **4**, 
- Be labelled with a pricing level of just above **2**,
- Be located roughly **2.45** km from the center of London.

We also discover that, in regards to London, no strong relationship exists between these metrics for our businesses. The strongest relationship we have is between the review count and the rating with a correlation-coefficiant value of -$0.2$, suggesting that as a business gets more reviews, the smaller it's rating value is (in a weak regard).

#### Category

Within the dataset, there exists a total of 108 separate business classification. The most frequent of these classification are:

1. Pubs (86)
2. British (62)
3. Indian (56)
4. Coffee & Tea (56)
5. Italian (45)

These category frequencies are distributed via a power law, with the above classification dominating the a significant proportion of all businesses collected. However, as stated prior, there exists a degree of ambiguity with the definition of categories. Many businesses could be allocated multiple classification types, yet is only given one. Thus, we must treat conclusion drawn using this data on a case-by-case bases.

Now that we have discovered the frquency of each business category in London, we can ask the following:

*Does the frequency of business categories influence the number of reviews each business category will receive?*

This question may seem to be trivial to answer, but we can present two approaches of logical reasoning that can explain if it does or does not. 

- Option A) The more businesses there are of a given category, the more opportunities the general public are given to leave a review (or a review at multiple locations).
- Option B) The more businesses there are of a given category, the less noval a businesses of this type is and thus the general public are less likely to leave a review.

So in order to answer this, we must consult the data. Indeed, the top categories for review counts are:

1. British (8169)
2. Indian (8029)
3. Pubs (7824)
4. Coffee & Tea (5492)
5. Italian (4138)

The five categories are the same for both rankings, suggesting that of our two arguments option A seems to explain how the general public behave. This argument is reinforced when we examine the entire list of categories with their respective review counts. After calculating the correlation-coefficient between these two variables, we get that this relationship is evaluated as $0.97$. This very strong relationship is illustrated when creating a scatter plot between each variable. Using this property, wehn can create an approximation which described their relationship as a direct proportion of each other as:

$$
N_{\text{reviews}} \approx \alpha \cdot f,
$$

where $\alpha$ can be interpretted as an *engagement* constant for how often each location will receive on average.

When can now try to calculate this $\alpha$ value to gain a measure of how much each category attracts the general public (assuming that the rate that a review is given is constant across the whole population). By simple deviding the number of reviews by the number of businesses for each category we yeild the following:

1. Flea Markets	(522)
2. Belgian (322)
3. Irish Pub (176)
4. Fish & Chips	(173.1)
5. Mexican (159.333333)

This data seems a bit suspicious that none of how previous top five categories are found and obscure categories are present. Suspicion is further increases when we calculate the average engagement rate across all categories London, with roughly $94.6$. (Note that is an average of each category which is itself a collection of businesses. If we want to find the average across each business which would be a better evaluation when considered per business-wise, use the average review count for each business which is presented above, $105$, which can be interpreted as the average engagement rate per business in London). This high metric value for these categories may be explain as simple have very few locations of this type. Indeed, we find that for *Flea Markets*, for example, only has one location. That location being the well-known 'Camden Market'. This would explain why they're ranked first since the location category is unique to them and it recieve a vast amount of customers during it's opening hours. So to gain a more reliable ranking of how often a business will recieve a review per location of a category we will restrict the ranking to categories which have a minimum number of businesses to 5. With this adjustment, our new ranking is:

1. Pizza,
    - av. reviews: 322,
    - locations: 20,
2. Vegan,
    - av. reviews: 173.1,
    - locations: 5,
3. Korean, 
    - av. reviews: 154.4,
    - locations: 6,
4. French,
    - av. reviews: 153.5,
    - locations: 31,
5. Cocktail Bars,
    - av. reviews: 153,
    - locations: 20.

#### Geo-Location

Regarding the distribution of businesses in London, we do see certain patterns emerging. For instance, it would be a safe assumption to say that businesses recorded by yelp would be spread out in a relatively uniform manner. However, we see that to make an assumption, we neglect to consider the verious parks in London, such as Hyde and Kensington, which disrupt this supposed uniform spread. The various parks across London are mostly located at roughly the same distance from the search center, which does explain the gap we see in the distribution of businesses by distance from the search center. Since on businesses are located within these parks, then the available space for a business to exist is reduced and would expect to a lower frequency of businesses at that distance. We can also observe other properties of the data by the other features of our businesses, such as price level and review count. Indeed,

- Although businesses with price levels of 1,2 and 3 are spread out across the London Area, businesses of price level 4 are located primarily within the inner city. This would indicate that this area is more affluent compared to the surrounding areas.
- We see that for our selection of businesses, the businesses that have a higher frequency of reviews left by customers are found within the center. We can attribute this to a higher foot-fall within the center of London compared to the outer regions of the city.
