# Music-Artist-Recommendation

#Data

The data is obtained from last.fm, hosted by grouplens -https://grouplens.org/datasets/hetrec-2011/
Since the idea is to recommend music artists by the number of plays and the user preferences, we will use user_artists.dat and artists.dat

#Data Wrangling and Exploration

We need to Merge both user_artists.dat and artists.dat using id and rename weight in user_artists.dat to playCount. 
And rank in descending order on how much each artists is played by the users
![mr1](https://user-images.githubusercontent.com/86455496/160304533-dd32bfa9-970d-4676-b93a-9477450b365f.png)



![mr2](https://user-images.githubusercontent.com/86455496/160304534-df229cbc-c2d0-4c45-8ef9-f53bb9610499.png)



![mr3](https://user-images.githubusercontent.com/86455496/160304542-1818cebd-e68c-43bc-a9fa-7a3d2e74f4d8.png)

Exploring the data set one important fact , we found is Britney Spears have more total artists plays however Lady Gaga have more unique users

#Recommender Systems

To use model based collaborative filtering technique which are based on matrix factorization. 
 one of the most used MF, Singular value decompoisiton (SVD) but since the data is very sparse , I used a different approach that to predict ratings by minimizing regularized squared error ( This is used in several other papers as well, especially related to recommendation systems) .Where K is a set of (u,i) pairs, r(u,i) is the rating for item i by user u and λ is a regularization term (used to avoid overfitting). The training of our model consists of minimizing the regularized squared error. After an estimate of P and Q is obtained, you can predict unknown ratings by taking the dot product of the latent features for users and items.
 
We have used stochastic gradient descent rather than alternating least squares in order to minimize the loss function.

#Train & Test

Created a new function for the split of train and validation, such that some of the items are removed from the data set and used in validation.
For each epoch , I ensured that cost function![mr4](https://user-images.githubusercontent.com/86455496/160304441-fab3167f-2961-4c5a-8fa3-55ec4a122476.png)
 is utilized to reduce the underfit and especially to reduce RMSE.

Thus to check our predictions we have created a specific list and user ids and have seen the predictions accordingly.

