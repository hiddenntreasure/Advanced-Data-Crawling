# Advanced Data Crawling
#Approaches:
First of all, I have used **warcio** library to iterate over the records of each archives. I have used several approaches to fetch data regarding *economic impact of covid 19*. I have run the code on colab platfrom. It is quite fast in fetching data from archives.
1. Initially, i tried to search by reading the title of each file. But it produced very few data regarding the topic.
2. Then, I tried to find link by keyword. But, almost all website has a navigation bar for covid or economic as well as there are suggested/external links. However, I tried to go for weight based approaches (the number of times covid or economic or its synonym appears). This approach also failed as few website repeated the keyword for other reasons. 
3. At last, I tried Natural Language Processing based approaches. Semantic Similarity is used as a metric. The approach is stated below:
_Install packages: **warcio** to 


#
