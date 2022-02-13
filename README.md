# Advanced Data Crawling
## Approaches:
First of all, I have used **warcio** library to iterate over the records of each archives. I have used several approaches to fetch data regarding *economic impact of covid 19*. I have run the code on colab platfrom. It is quite fast in fetching data from archives.
1. Initially, I tried to search the Query by keyword in the title of each record. But it produced very few data regarding the topic.
2. Then, I tried to find query by keyword in the whole data of each record. But, almost all website has a navigation bar for covid or economic as well as there are suggested/external links. However, I tried to go for weight based approaches (the number of times covid or economic or its synonym appears). This approach also failed as few website repeated the keyword for other reasons. 
3. At last, I tried Natural Language Processing based approaches called document/sentence similarity. To measure similarity, cosine similarity is used as a metric. The approach is stated below:
  - Install packages:
    - **warcio** : to fetch file and iterate over the records
    - **sentence-transformers** : to compute dense vector representations for sentences, paragraphs in short embedding.
    - **BeautifulSoup and PorterStemmer** : for cleanning of the data
  - I used a comparison between [wikipedia's article](https://en.wikipedia.org/wiki/Economic_impact_of_the_COVID-19_pandemic) and all the html formated records. Basically, I spilt the wikipedia's article by topic like impact on business, sport, regions; total 44 topic. If you go through the article you will get an idea. Even i compared the whole wikipedia's artilce with each records. However, I get the best result by splitting the articles.
  - At first, I cleaned both the data of wikipedia's article and the each feteched record.
  - Then convert data of the record into vector that's mean embedded the data by using **sentence_transformer**. There are many pre-trained model for sentence/paragraph embedding as shown in the below picture: 
![Models along with the performance](https://miro.medium.com/max/1154/1*P2zYNp3-nR28zraavajMyA.png)
  - In this study, I have used cosine similarity as a metric. The threshold value was 0.75.
  - I have compared each wikipedia's topic (44 topic) with the iterated record. So, there are 44 similarity index, but i took the similarity index which is greater than 0.75 and maximum among all.
  
## Performance of NLP based approach:
- It can correctly detect website which is related economy.
- However, I am afraid the number website related to "impact of covid in economy" is not satisfactory.

## Limitations:
In this section, I will discuss all the approaches limitation as well as mine.
- Due to the huge size of each month archives, it is difficult to understand the data more clearly. But, I found that each record in the WARC contains a html with its infomation such as link.
- I don't have any previous idea about common-crawl. Moreover, there are very few articles related to it. Even it tooks one whole day to create the programming environment. However, the work goes in vain, I had to work in the regular colab platform where I have to run same code specially for warcio multiple times; even sometimes it crash.
- Searching keyword in each file's title produced very few output. I assumed there are very few articles which title is related to the query.
- Html record contains external links, drop down menu and navigation bar along with the main article. So, searching by keyword was a bad idea.
- Colab system crash after sometimes due to bigger size of the file. Thats why i couldn't run through all 2020 archives.

## References:
1. https://towardsdatascience.com/semantic-similarity-using-transformers-8f3cb5bf66d6
2. https://towardsdatascience.com/calculating-document-similarities-using-bert-and-other-models-b2c1a29c9630
3. https://www.irjet.net/archives/V8/i4/IRJET-V8I4927.pdf
4. https://towardsdatascience.com/cutting-edge-semantic-search-and-sentence-similarity-53380328c655
5. https://www.analyticsvidhya.com/blog/2020/08/top-4-sentence-embedding-techniques-using-python/
