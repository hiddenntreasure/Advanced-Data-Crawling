# Advanced Data Crawling
## Approaches:
First of all, I have used **warcio** library to iterate over the records of each archives. I have used several approaches to fetch data regarding *economic impact of covid 19*. I have run the code on colab platfrom. It is quite fast in fetching data from archives.
1. Initially, i tried to search by reading the title of each file. But it produced very few data regarding the topic.
2. Then, I tried to find link by keyword. But, almost all website has a navigation bar for covid or economic as well as there are suggested/external links. However, I tried to go for weight based approaches (the number of times covid or economic or its synonym appears). This approach also failed as few website repeated the keyword for other reasons. 
3. At last, I tried Natural Language Processing based approaches called document/sentence similarity. To measure similarity, Semantic Similarity is used as a metric. The approach is stated below:
  - Install packages:
    - **warcio** : warcio to fetch file and iterate over the files
    - **sentence-transformers** : to compute dense vector representations for sentences, paragraphs in short for embedding.
    - **BeautifulSoup and PorterStemmer** : for cleanning of the data
  - I used a comparison between ![wikipedia's article](https://en.wikipedia.org/wiki/Economic_impact_of_the_COVID-19_pandemic) and all the html formated data. Basically, i spilt the wikipedia's article by topic like impact on business, sport, regions. If you go through the article you will get an idea. Even i compared the whole wikipedia's artilce with each data from monthly archives. However, i get the best result for topic base comparison of the articles.
  - Firs of all, I cleaned both the data of wikipedia's article and the each feteched data.
  - Then convert the data into vector that's mean embedded the data by using **sentence_transformer**. There are many pre-trained model for sentence/paragraph similarity prediction as shown in the below picture: 
![Models along with the performance](https://miro.medium.com/max/1154/1*P2zYNp3-nR28zraavajMyA.png)
  - In this study, I have used cosine similarity as a metric. The threshold value was 0.75.
  
## Performance of NLP based approach:
- It can correctly detect website which is economic related.
- However, I am afraid the number website related to "impact of covid in economic" is not satisfactory.

## Limitations:
In this section, I will discuss both approaches limitation as well as mine.
- Due to the huge size of each month archives, it is difficult to understand the data more clearly. But, I assumed that each file in the WARC contains a html with its infomation such as link.
- I don't have any previous idea about common-crawl. Moreover, there are very few articles related to it. Even it tooks one whole day to create the programming environment. However, the work goes in vain, i had to work in the regular colab platform where i have to run same code specially for warcio related multiple even sometimes crash.
- 
