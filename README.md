# Building a recommendation system

## Possible approaches

### Content based 
  They try to recommend products that have similar attributes to a product that the user already liked.

  Perspectives
  * TFIDF Version: Calculates words frequence for each product. We then build an user profile compiling word's relevance. Finally, score products by summing (word's score from products X word's score from users)
  * Non-Negative Matrix Factorization (NMF) Version: extract topics from the vector description. Like the TFIDF version, we can now deduce a user’s profile based on the NMF topics values.

### Collaborative filtering
  Collaborative filtering systems make recommendations only based on how users rated products in the past, not based on anything about the products themselves.

  Rating may be implemented in several ways, such as: 
  * number of visits
  * time spent visiting
  * time spent since last visit

  Perspectives
  * Given user A, find top similar users set U (users with similar same products's rating), for each user u in U, recommend u's top rated products to A
  * Given product A, find top similar products set P (products with similar same users's rating), for each product p in U, recommend p's top rated.

### Mixing These Approaches
  make some “average” of these different scores to compute our final affinity User/Product. 

  * Machine Learning
    Negative sampling: you will have to create User/Product couples that are “false” (i.e., the user didn’t buy the product during the period). For each couple, your features will be the affinity scores you just computed, and the target will be “true” or “false”. You try to find the best combination to optimise the visits, buys, and likes.
    Creating false couples: 
    * Randomly, but only picking users that visited, bought, or liked at least one thing during the period. We don’t pick users with only negative examples during that period because otherwise it would be too easy to have a good score, and it would not be very relevant.
    * Excluding couples that happened in the past (if someone already bought something you don’t want to penalize it). We don’t take as fake example a true example from the past.

## Common tech stack

### Python libs

* SciPy
* NumPy
* pandas