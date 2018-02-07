# Recommendation-Engine

Two most ubiquitous types of recommender systems are Content-Based and Collaborative Filtering (CF). Collaborative filtering produces recommendations based on the knowledge of users’ attitude to items, that is it uses the “wisdom of the crowd” to recommend items. In contrast, content-based recommender systems focus on the attributes of the items and give you recommendations based on the similarity between them.

In general, Collaborative filtering (CF) is the workhorse of recommender engines. The algorithm has a very interesting property of being able to do feature learning on its own, which means that it can start to learn for itself what features to use. CF can be divided into Memory-Based Collaborative Filtering and Model-Based Collaborative filtering. In this tutorial, 
we will use MovieLens dataset, which is one of the most common datasets used when implementing and testing recommender engines. It contains 100k movie ratings from 943 users and a selection of 1682 movies. we should add unzipped movielens dataset folder to your notebook directory.


A distance metric commonly used in recommender systems is cosine similarity, where the ratings are seen as vectors in nn-dimensional space and the similarity is calculated based on the angle between these vectors. Cosine similiarity for users aa and mm can be calculated using the formula below, where we take dot product of the user vector ukuk and the user vector uaua and divide it by multiplication of the Euclidean lengths of the vectors.

scosu(uk,ua)=uk⋅ua∥uk∥∥ua∥=∑xk,mxa,m∑x2k,m∑x2a,m√
sucos(uk,ua)=uk⋅ua‖uk‖‖ua‖=∑xk,mxa,m∑xk,m2∑xa,m2

To calculate similarity between items mm and bb you use the formula:

scosu(im,ib)=im⋅ib∥im∥∥ib∥=∑xa,mxa,b∑x2a,m∑x2a,b

we have already created similarity matrices: user_similarity and  item_similarity and therefore we can make a prediction by applying following formula for user-based CF:

x^k,m=x¯k+∑uasimu(uk,ua)(xa,m−x¯ua)∑ua|simu(uk,ua)|
