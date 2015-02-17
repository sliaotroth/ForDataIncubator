# ForDataIncubator

####THE QUESTIONS

Aloha Data Incubator! My project proposal center around manager responses to customer online reviews:

Quantifying manager response data:

  What are the different kinds of manager responses, based on tone/content (sentiment) – e.g. can thank you responses, apologies, offers for restitution, or reasonable explanations be categorized consistently? How frequently are managers responding for each business? How many businesses with online reviews have manager responses?

Is there a correlation between manager responses to customer online reviews and:

  The subsequent usefulness of the review to others? The subsequent overall number of reviews for a given business? The subsequent overall opinion of reviews? The subsequent aggregate ranking of the business?


Is there a better way for managers to write responses - are there predictive patterns related:

  The quickness of response? The length of response? The tone/content (sentiment) of the response? Specific keywords in the response? The frequency of responses for each business?

####THE PROBLEM

Online reviews for firms and their services proliferate on sites such as Yelp, TripAdvisor, Expedia, and Hotels.com. The reviews reflect a semi-enduring voice of the customer and are readily seen by other (potential) customers. Negative reviews are generally considered to be detrimental to a company’s brand, to their online reputation, and to their relationships with other customers. 

If a company receives a negative review, what should managers do? Some sites (such as TripAdvisor) allow managers to respond to individual reviews. Should they respond to or ignore a negative review? If they do respond, what should they say? Are there tactics, keywords, or content that would work better than others to mitigate the impact of a negative review? Suggestions for companies are fairly general and may be limited in their usefulness in guiding managers on what to do. Entrepreneur suggests that a response should be diplomatic and consistent. Yelp, in a blog post on “Tactics for Responding to Online Critics”, suggest making a private response before making a public one. Hotel News Now (a hospitality trade publication) suggests that hotel managers should respond to all online reviews in order to show commitment to customers. TripAdvisor appears to agree, but tells each manager that they should determine their own strategy for responding. 

There is a cost for managers to respond. From an opportunity cost perspective, managers must take time from “managing” to write authentic, sincere, detailed responses. Depending on the amount of review traffic, this could be a full time endeavor for any one individual. From a brand/online reputation/customer relationship management perspective, a response could hit the wrong note for any potential customer who reads the review/response. Indeed, there are numerous online articles along the vein of “hotel managers who left jerky responses on TripAdvisor” or “you wouldn’t believe how this hotel manager responded…“. 

An analysis of customer review data and corresponding manager response review could provide actionable information for not only managers but for sites hosting the reviews. Is there an opportunity for businesses to engage in service recovery? If so, how?  How do review sites help facilitate these actions?

####GENERAL ANALYSIS

One the raw data is obtained, cleaned, and formatted appropriately, my general analysis plan would be to conduct a sentiment analysis to categorize both customer reviews and manager responses. Once categorized, the data can be examined for correlations with rankings, ratings, or positive/negative valence of the text review over time, helpful votes, depending on customer review and manager response occurrences.

####RELEVANCE AND USEFULNESS

Understanding manager responses can help guide firms in service recovery and brand management. Analysis of online reviews is increasing as a way for firms to measure customer engagement, and an extension of this logic should apply to manager responses as a way to the firm to engage with their customers. Having more information along this vein could help firms avoid reputation damaging pitfalls (responding inappropriately or ineffectively), or could help improve online review ratings, which may have a financial return on investment as online review scores are suggested to impact conversion and pricing. For example, one Cornell Hospitality Report (Nov 2012) suggest that a 1-point increase in user review score (on a 5-point scale) would allow a hotel property to increase their price by 11.2 percent and maintain the same market share. The better the “reputation”, the higher the occupancy and revenue per room. What if managing responses to online reviews can impact review scores?

Lastly, for those sites who host user reviews, there should be benefit in understanding the role manager responses play in the usefulness of reviews and could help in personalizing the information a visitor views.

####DATA SOURCE(S)

Hotel reviews are appropriate for this project, as these reviews are numerous and related manager responses are available on sites such as TripAdvisor. 

I began by exploring publicly available datasets for hotel reviews. The LARA (Latent Aspect Rating Analysis) dataset from Wang and colleagues include reviews crawled from TripAdvisor (from approximately 2003 through 2009), but looking at the dataset, I verified that it does not include manager responses. Likewise, the OpinRank dataset from Kavita Ganesan includes hotel reviews but no manager responses.

Ideally, data for this project will have to be extracted from the existing TripAdvisor site, and should include manager responses matched to customer reviews, rankings, date stamp, text of reviews, information on businesses and reviewers.

So far, I have had mixed success with pulling data from TripAdvisor. This part of the project is curretly in progress. As a result, I have started working with a small sample, as a proof of concept.


####EXPLORATORY DATA ANALYSIS - START WITH PROOF OF CONCEPT

I extracted data for one sample market (Honolulu, HI), to better understand the data I would be looking at and to gain experience with the process of data gathering, cleaning, and analysis.

According to TripAdvisor's Honolulu page, there are 82 hotels classified in the Honolulu area.

I started looking at the data to identify outliers and funny instances.

####Plots are located at: https://github.com/sliaotroth/ForDataIncubator/issues/1

Plot: TripAdvisor Honolulu Hotel Stars by Ranking
Plot: TripAdvisor Honolulu Hotel Stars by Number of Reviews

Of the 82 hotels, 2 hotels have no reviews (Hotel ranked #81, #82), 3 hotels have less than 10 reviews (Hotel ranked #74, #78, #79), and 1 is not open to the general public as it is located on an active Army base (Hotel ranked #80). These 6 hotels were excluded from the working set, leaving 76 hotels.

Plot: Distribution of HNL Hotels by TripAdvisor Stars

Of the 76 hotels in the dataset, no hotel has 5 stars, about 20% have 4.5 stars, about 50% of the hotels have 4 stars, and about 18% have 3.5 stars.

Plot: Distribution of any Manager Response Activity within 3 Pages

Overall, 55 out of 76 hotels (72%) show some type of manager response within 3 pages of the most recent review (includes approximately the last 21 reviews). For hotels with reviews added consistently to the site, this encompasses approximately a 2 to 3 week period. There is some variance within a star category. Hotels with lower stars may or may not have manager responses. Of the hotels with 3.5 or 4.5 stars, approximately 76-79% have manager responses. 71% reviews for hotels with 4 stars (the largest category) include manager responses.



I collected review level data for the top 5 hotels, of the most recent 49 reviews. This gave me a sense of the data available and what I will need to do on a mass scale to prepare the data for analysis.

Overall, I have been able to identify the following variables:

TripAdvisor Data on Honolulu market:
Name, 
Rank, 
Stars, 
NumReviews, 
NumRatingExcellent, 
NumRatingVeryGood, 
NumRatingAverage, 
NumRatingPoor, 
NumRatingTerrible, 
PercentRatingExcellent, 
PercentRatingVeryGood, 
PercentRatingAverage, 
PercentRatingPoor, 
PercentRatingTerrible, 
NumReviewsforFamilies, 
NumReviewsforCouples, 
NumReviewsforSolo, 
NumReviewsforBusiness, 
PercentReviewsFamilies, 
PercentReviewsCouples, 
PercentReviewsSolo, 
PercentReviewsBusiness, 
RatingLocation, 
RatingSleepQuality, 
RatingRoom, 
RatingService, 
RatingValue, 
RatingCleanliness, 
NumTravelerRoomTips, 
PriceRangeAvgRates, 
HotelClass5star, 
NumRooms, 
MgrReviewsonpg1, 
MgrReviewsonpg2, 
MgrReviewsonpg3, 
FirstThreeMgrReview, 
AnyMgrReview, 
Address, 
URL

TripAdivsor most recent 49 reviews for hotels ranked 1 through 5:
UserLocation, 
UserName, 
UserNumPriorReviewHotel, 
UserNumReviews, 
UserPriorReviewStar, 
UserReviewsInMarket, 
UserRole, 
UserTotalHelpfulVotes, 
UserTotalReviewCities, 
UserTotalReviewsHotel, 
ReviewDate, 
ReviewNumHelpful, 
ReviewRoomTipText, 
ReviewStars, 
ReviewStarsCleanliness, 
ReviewStarsLocation, 
ReviewStarsRoom, 
ReviewStarsService, 
ReviewStarsSleep, 
ReviewStarsValue, 
ReviewStayedDate, 
ReviewText, 
ReviewTitle, 
ReviewTraveledAs, 
MgrName, 
MgrRespDate, 
MgrRespText, 
MgrTitle, 
UserLocation, 
UserName, 
UserNumPriorReviewHotel, 
UserNumReviews, 
UserPriorReviewStar, 
UserReviewsInMarket, 
UserRole, 
UserTotalHelpfulVotes, 
UserTotalReviewCities, 
UserTotalReviewsHotel, 
ReviewDate, 
ReviewNumHelpful, 
ReviewRoomTipText, 
ReviewStars, 
ReviewStarsCleanliness, 
ReviewStarsLocation, 
ReviewStarsRoom, 
ReviewStarsService, 
ReviewStarsSleep, 
ReviewStarsValue, 
ReviewStayedDate, 
ReviewText, 
ReviewTitle, 
ReviewTraveledAs, 
MgrName, 
MgrRespDate, 
MgrRespText, 
MgrTitle

Plot: Hotels Ranked 1 through 5, Distribution of Manager Response Activity

Plot: Hotel #1, Distribution of Manager Response Activity

Plot: Hotel #2, Distribution of Manager Response Activity

Plot: Hotel #3, Distribution of Manager Response Activity

Plot: Hotel #4, Distribution of Manager Response Activity

Plot: Hotel #5, Distribution of Manager Response Activity


Most reviews for these hotels are given 5 stars. For these 5 hotels there are manager responses to 25% of the 5 star reviews, 31% of the 4 star reviews, 15% of the 3 star reviews, 0% of the 2 star reviews, and 43% of the 1 star reviews. However, it is only Hotel 1 and Hotel 3 that exhibit manager responses. Hotel 1 appears to respond to most reviews (98%), and these seem to be overwhelmingly positive (4 and 5 stars). Hotel 3 show some negative reviews (1 star) and the manager appears to respond to those as well as to postitive reviews (4 or 5 stars).

###CONCLUSION FROM EXPLORATORY DATA ANALYSIS

Assembling and cleaning the data will take time. Also, gathering information on specific variables such as manager response data may not be easily available through available API, leaving html scraping methods.

Next steps are to take the text information and begin to categorize the reviews.

Thank you for reading!





