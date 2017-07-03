# RecommenderSystem

It's an online movie recommender system based on Hadoop framework. Dataset comes from **Netflix**. This system will recommend similar movies based on user's previous preferences. It's an individual project.

The main algorithm based on **Item Collaborative Filtering**. Generate **co-ocurrence matrix** and rating matrix from the raw dataset then merge them to get the recommender list for different users. The whole project took several steps and **5 MapReduce** processes. Used **Docker** to simulate the **large-scale Hadoop computing environment**.

## Why Item Collaborative Filtering algorithm?

**A co-occurrence matrix is a matrix that is defined over an image to be the distribution of co-occurring pixel values (grayscale values, or colors) at a given offset.**

First, the amount of movies on Netflix is far less than user amount. It would be a easier and effiency way to calculate based on item relations.

Second, the similarity between movies won't change too much as time going. It would be effiency and more accurate to determine movies since they change slower than users.

Last, item collaborative filtering algorithm will use user's historical data which can be more convincing than recommend movies from someone that love the same movie.

## How to determine similarity between items(movies)?

There are many aspects deserve considering, mainly two general approaches:

Based on user's profile
- watching history
- rating history
- favorite list
- ...

Based on movie's info
- movie genre, category ...
- movie producer, director, cast, theme ...
- ...

In this project, I mainly used rating history.

First, it would be easy to quantify impacts by rating scores rather than determine genre or director's impact on the movie.

Second, data like watching history would be inaccurate in some cases. For example, some people may watch an movie but don't really interested in it.

Last but not the least, I built this recommender system demo just to demonstrate the possibility of data analysis and I can add other dimensions into account at any time with the same approach.

## Steps


1. Pre-process raw data to get relation matrix of rating history of each user and movies.
2. Generate co-ocurrence matrix by above dataset using the first MapReduce process, which called CoOccurrenceMatrixGenerator in source file.
3. Normalize the co-ocurrence matrix.
4. Build rating matrix.
5. Multiply co-ocurrence matrix and rating matrix.
6. Generate commender list.

## Detailed Algorithm Breakdown

![image1](https://github.com/yuanfanz/RecommenderSystem/blob/master/image/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202017-06-30%2014.46.06.jpg)

![image1](https://github.com/yuanfanz/RecommenderSystem/blob/master/image/屏幕快照 2017-06-30 14.46.23.jpg)

![image1](https://github.com/yuanfanz/RecommenderSystem/blob/master/image/屏幕快照 2017-06-30 14.46.32.jpg)

![image1](https://github.com/yuanfanz/RecommenderSystem/blob/master/image/屏幕快照 2017-06-30 14.46.43.jpg)

![image1](https://github.com/yuanfanz/RecommenderSystem/blob/master/image/屏幕快照 2017-06-30 14.46.48.jpg)

![image1](https://github.com/yuanfanz/RecommenderSystem/blob/master/image/屏幕快照 2017-06-30 14.46.54.jpg)

![image1](https://github.com/yuanfanz/RecommenderSystem/blob/master/image/屏幕快照 2017-06-30 14.47.26.jpg)

![image1](https://github.com/yuanfanz/RecommenderSystem/blob/master/image/屏幕快照 2017-06-30 14.47.31.jpg)

![image1](https://github.com/yuanfanz/RecommenderSystem/blob/master/image/屏幕快照 2017-06-30 14.47.35.jpg)

![image1](https://github.com/yuanfanz/RecommenderSystem/blob/master/image/屏幕快照 2017-06-30 14.47.39.jpg)

![image1](https://github.com/yuanfanz/RecommenderSystem/blob/master/image/屏幕快照 2017-06-30 14.47.44.jpg)
