# Restaurant-Recommendor-System
Built knowledge based and content based Recommendor System using the data Scraped from Zomato.

### Refer the Link below to find Python Script used to Scrape Zomato Data 
https://github.com/tanu-seth/Zomato-Restaurant-Scraper-Python


### Goal : 
To build restaurant recommendor system for restaurants in Cincinnati.

### Approach :
I will be working on two approaches to build recommendor system:

**Knowlege Based Recommendor System** 
Knowledge based recommendors are not the first choice for building restaurant recommendor for Zomato. But since our data was scraped and we do not have individual user rating info and details, we cannot implement collaborative filter which would be the optimal solution for this case.

These recommenders are used for items that are very rarely bought. It is simply impossible to recommend such items based on past purchasing activity or by building a user profile. Take real estate, for instance. Real estate is usually a once-in-a-lifetime purchase for a family. It is not possible to have a history of real estate purchases for existing users to leverage into a collaborative filter, nor is it always feasible to ask a user their real estate purchase history.


This will be a simple recommendor system that will perform the following tasks. Ask the user for her/his preferences of :

* Locality
* Cusinies
* Budget for restaurant

**Content Based Recommendor System**
Content-based recommenders suggest similar items based on a particular item. This system uses item metadata, such as Locality, Cuisine, rating, etc. for restaurants, to make these recommendations. The general idea behind these recommender systems is that if a person liked a particular item, he or she will also like an item that is similar to it. We would recommend restaurants similar to the one searched by the user. Our recommender system is highly dependent on defining an appropriate similarity measure. Eventually, we select a subset of restaurants to display to the user.

We will be working on the locality , cuisine , cost_for_two and rest_name to find similarity between restaurants. Since the restaurant name might not actually be similar for two restaurants as there are quite a few unique names, we will give less weightage to the restaurant name while making the soup and more weightage to locality , cost_for_two and cusines.

Steps to create content based recommendor system:
* Declare the restaurant name as an argument.
* Obtain the index of the restaurant name from the indices reverse mapping.
* Get the list of cosine similarity scores(similarity scores between the metadata -  cuisine, locality, restaurant name) for that particular restaurant with all resturants using cosine_sim. Convert this into a list of tuples where the first element is the position and the second is the similarity score.
* Sort this list of tuples on the basis of the cosine similarity scores.
* Get the top 10 elements of this list. Ignore the first element as it refers to the similarity score with itself.
* Return the restaurant details corresponding to the indices of the top 10 elements, excluding the first.
