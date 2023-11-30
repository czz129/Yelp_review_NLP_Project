# Yelp_review_NLP_Project - The Degree of Informativeness of Yelp Business Reviews 

## Introduction:

Both customers and business owners on Yelp depend on reviews to gauge the quality of various experiences. Customers read reviews to obtain detailed information about businesses, while proprietors utilize reviews to gather feedback and implement improvements. In this project, our primary focus is on annotating the degree of informativeness in Yelp business reviews from the perspective of potential users.
An informative review is clear, factual, and aims to help potential customers gain a comprehensive understanding of the experience offered by a business. Such reviews should be detailed, specific, and honest, highlighting the pros and cons of various aspects such as quality, service, ambiance, and pricing. Furthermore, these reviews should identify areas for potential enhancement. In contrast, less informative reviews might be opinionated without substantiating evidence or lack sufficient insights for potential customers to make informed decisions.
In the subsequent sections, we will delineate the rating scale, furnish examples of reviews with varying degrees of informativeness, and provide tips for ensuring consistency and accuracy in your annotations. By adhering to these guidelines, you will contribute to enhancing the overall quality and utility of Yelp business reviews for users in search of reliable and informative recommendations.

## Basic Concepts:
Informativeness and helpfulness are terms often used in the context of online reviews. They refer to distinct aspects of a review's value, though they can be closely related. Here are the definitions for each term:
**Informativeness**: Informativeness refers to the extent to which a review provides relevant, valuable, and factual information about the subject matter. In the context of business reviews, this would include details about the quality, service, ambiance, pricing, and any other factors that contribute to the overall dining experience. A highly informative review presents a comprehensive and accurate account of the experience, enabling readers to form a clear understanding of the business's offerings, strengths, and weaknesses.
**Helpfulness**: Helpfulness, on the other hand, pertains to the degree to which a review assists readers in making informed decisions based on the provided information. A helpful review effectively addresses the concerns or questions potential customers may have, offering insights that are directly applicable to their decision-making process.
## Detailed Guidelines:
Informativeness is constructed on the spectrum from 0-5, with 0 being not informative at all and 5 being the most informative. To break down the composition of each review we have defined 5 important criteria for a review, each of such criteria contributes to a point if the review hit it:

The review comments on the good/bad quality of the environment of the business (eg. size, cleanness, vibe, construction style):
- “You would think from the size of the place it would be good for groups” [size]
- “Clean, comfortable, and well-managed.”[cleanness]
- “I like the vibe of this place and it's close and convenient to where i live, so I really want to like it, but I just wasn't thrilled with it the first time.”[vibe]
- “We had this private booth which was very romantic and nice. I think this place would be good for people who want privacy and have plenty of time for dinner.” [construction style]

The review comments on the good/bad quality of products the business (eg. tasteful, awful, mediocre, price, not useful):
- “I had the costanza, and the fillings were tasty, but the crust was disappointing. It was way too bread-y, as opposed to doughy, and when I think of a calzone, I think of dough like pizza dough- this was not that.” [tasteful]
- “I ordered the black spaghetti that other patrons raved about. It was pretty disgusting. I'm not sure why he had some a weird texture and almost tasted like plastic. I've tried many different types of spaghetti and this by far was the worst plate I've tried.”[awful]
- “Service was crappy, and food was mediocre.  I wish I would have picked some other place for my last dinner in town.” [mediocre]
- “Coming from TN, I chose to purchase this vehicle from Glanzmann due to its limited availability and attractive price. I communicated with sales on numerous occasions before committing to purchase from Glanzmann nearly 1000 miles from home.” [price]

The review comments on the good/bad quality of the service of the business (eg. good manner, bad attitude, extraordinary experience):
- “Joann is probably my favorite- she's friendly, attentive, funny, and I've really gotten to know her, and I'd give them 5 stars if my experience was with her alone. ”[good manner]
- “There is a bartender named Nikki though, and if she's there, I always get the worst service. She barely checks on me/us to see how we're doing, she seems unfriendly, if she actually comes to refill your chips then she will not refill your salsa, she has taken my beer and refilled it without asking (when I was done and trying to leave), and I've had to wait forever to ask her for my check…” [bad attitude]
- “Terrible customer service. I've been three times and I've had two different older waitresses. Not pleasant to deal with whatsoever. The owner on the other hand is lovely.”[bad attitude]

The review comments on the delighters/disgusted quality of the business (eg. Any excited experience from the business, additional free services, waiting time, safety issues, additional charges, environmental friendly):
- “First off, they get bonus points for serving FREE edemame as an appetizer. I usually pay $4 to $5 for it at other sushi restaurants.” [additional free services]
- “ First, I didn't make a reservation and we waited about 50 minutes to be seated when they told us it will be about 15 to 20 min wait. I probably should'v left and tried the next time since I was not happy when I was seated due to the waiting.” [waiting time]
- “ It started to rain with thunder and lightning so we did not see any alligators because we had to go back for safety reasons. We did try to see some alligators but they don't come out if it's cold. Don't book your tour if it's cold or storming and I'm sure it will be a 5 star tour for you.” [safety issue]
- “ My suggestion is they need to cook their meat longer and ensure it reaches optimum 165°F Temp, serve the food very hot temp to ensure bacteria are dead, and only source their greens and veggies from USA only sources. Avoid Mexico as they have big issues with water pollution cross-contamination.” [safety issue]

The review provides information about how the business can be improved on its different qualities mentioned above (eg. suggestions on how each experience can be better):
- “ I'd like to see Susanna improve upon some of her traditional recipes by either adding new flavors or perhaps returning to her Chinese roots with a more ethnic menu. I'm hoping there will be a revitalization and that I will come to love Susanna Foo as much as I did as a child.” [future improvement]
- “The food is average and for the price of drinks - it would be a great place to hang if the service improves.”  [improvement]
- “Overpriced for what you get. I think this is a cute spot to meet up with a friend, but that's about it. I prefer my own homemade coffee to be honest. Adorable concept, just could use some improvement to products offered and prices.” [improvement]


Note: If a review is not specific about the business, it receives a 0.
- “Good service, nice foods”
- “An awful experience with the restaurant.”
- “Can't go wrong with some Todd Cobell!”
- “Great ambiance!  “
- “3.5 stars.”
## Sample feature:
To avoid the “informativeness” to “helpfulness” we controlled the “helpfulness” by only using reviews that have 3 stars (an original range from 0 to 5).

### Our Approach

1. **Pre-Implementation Analysis**: Before implementing our model, we explored various baseline methods on our data. Ordinal regression showed the highest base accuracy, but we decided to proceed with a BERT model as it demonstrated higher accuracy with feature addition.

2. **Data Preprocessing**: A significant step in our approach was cleaning the input data. This included removing punctuation, tokenization, removing stopwords, and lemmatization. The cleaned text was then used for further processing.

3. **Initial Model Training**: We initially utilized a Logistic Regression model with TF-IDF (Term Frequency-Inverse Document Frequency) for classifications. This model yielded a base accuracy of 0.55.

4. **BERT Model Implementation**: We progressed to training a BERT (Bidirectional Encoder Representations from Transformers) model. The BERT model was chosen for its effectiveness in understanding the context of a word in a sentence.

5. **DistilBERT Integration**: After the BERT model, we experimented with DistilBERT, a distilled version of the BERT model that maintains most of the original model's accuracy but with fewer parameters. This was done to improve the model's performance further.

6. **Combined Model Development**: We then developed a combined classifier integrating both BERT and DistilBERT models. The combined model aimed to leverage the strengths of both individual models, thereby improving the overall prediction accuracy.

7. **Final Model and Evaluation**: The final combined model showed a test accuracy of 0.70. To understand our model's performance in detail, we created a confusion matrix and other evaluation metrics to assess its accuracy and reliability.

## Model Evaluation:
### Evaluation

In evaluating our BERT model's performance, we identified several key factors affecting its accuracy, particularly for high informativeness labels:

1. **Limited Sample Size**: The model's underperformance on labels 4 and 5 can be partly attributed to the extremely limited number of samples for these labels in our dataset. With only one sample of label 5 and ten samples of 0, the model lacked sufficient data to effectively learn and predict these categories.

2. **Token Size Limitation**: Our choice of a maximum token size of 256, constrained by GPU resources, likely impacted the model's ability to fully capture the essence of longer reviews. Since higher informativeness is associated with longer text, this limitation might have led to higher informativeness reviews being misclassified.

3. **Annotation Guidelines Flaw**: Our annotation method, which capped the points a review could earn regardless of how many times it discussed a category, resulted in a learning imbalance. This skewed the model's understanding towards reviews that include more adjectives, even if they weren’t necessarily more informative.

4. **Systematic Classification Errors**: The model systematically misclassified reviews with informativeness of 1 and 5. For example, reviews with basic suggestions for improvement were often erroneously scored as highly informative (5), indicating a gap in the model's understanding of what constitutes a comprehensive and informative review.

### Conclusion

Our project's journey in developing a BERT model to assess the informativeness of Yelp reviews has been enlightening, revealing both the potential and limitations of current NLP technologies. The insights gained from this project underscore the importance of a robust and representative dataset, the need for carefully crafted annotation guidelines, and the challenges inherent in capturing the subtleties of human language and sentiment.

Going forward, improvements in our approach could include expanding the dataset to include more examples of higher informativeness levels, optimizing the token size for more comprehensive review analysis, refining our annotation guidelines to better capture the depth of informativeness, and enhancing the model’s ability to interpret complex language structures such as sarcasm.

This project has not only advanced our understanding of NLP in practical applications but also highlighted the critical need for continuous evaluation and iteration in the development of machine learning models. It exemplifies the dynamic interplay between data, model design, and real-world application, offering valuable lessons for future endeavors in the field of NLP and data analytics.
