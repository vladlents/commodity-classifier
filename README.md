<!-- This is the markdown template for the final project of the Building AI course, 
created by Reaktor Innovations and University of Helsinki. 
Copy the template, paste it to your GitHub README and edit! -->

# Project Title: Commodity code-classifier

Final project for the Building AI course

## Summary
# Describe briefly in 2-3 sentences what your project is about. About 250 characters is a nice length! 
The project is about building a commodity classifier that will help the importer select the correct [Harmonized System (HS) code](https://www.trade.gov/harmonized-system-hs-codes) upon import into the country. The classifier is trained to predict the HS code using historical data about previously declared products. For each new product, it can predict the HS code based on the product description. 

## Background

# Which problems does your idea solve? How common or frequent is this problem? What is your personal motivation? Why is this topic important or interesting?

This solution can help solve a number of problems that arise when importing goods, in particular:
* to help importers in selecting correct product group from the the Harmonized System (HS) while declaring goods;
* to identify misdeclared goods due to unintended errors;
* to prevent deliberate fraud on imported goods;
* to increase accuracy of product classification;
* to automate the product classification procedure;
* to optimize supply chains and improve compliance with customs regulations.
The motivating factors are to share knowledge about possible practical applications of innovative machine learning techniques in traditional industries and support the learning process.  

## How is it used?
# Describe the process of using the solution. In what kind situations is the solution needed (environment, time, etc.)? Who are the users, what kinds of needs should be taken into account?

In practice, the solution can be used by customs brokers or other importing actors to select the correct HS code group for their product on a declaration or invoice. It will work by using the trained Word2Vector model from one hand and the textual description of goods provided by the consignor from another hand. Since the HS code is used for calculation of customs duties and regulatory compliance, it is crucial for the importer to have the HS code correctly declared and consistent with the goods description. 

This is how you create code examples:
```
def main():
   countries = ['Denmark', 'Finland', 'Iceland', 'Norway', 'Sweden']
   pop = [5615000, 5439000, 324000, 5080000, 9609000]   # not actually needed in this exercise...
   fishers = [1891, 2652, 3800, 11611, 1757]

   totPop = sum(pop)
   totFish = sum(fishers)

   # write your solution here

   for i in range(len(countries)):
      print("%s %.2f%%" % (countries[i], 100.0))    # current just prints 100%

main()
```

## Data sources and AI methods
Since computers can process data in digital format only, the solution needs to translate product descriptions (free-text sentences) into numeric vectors. This method is known as word to vector (Word2Vector). For this purpose, the solution will use a pre-trained word embedding model provided by Google. 
Then it will count the number of clusters formed by the vectors in the same HS code group and calculate a central vector for each cluster. The central vector represents the arithmetic mean of product descriptions belonging to the cluster. For simplicity, we will consider one cluster per HS code group. As a result, we will get a model that is a table containing vectors associated with groups of HS codes.   
With the computed Word2Vector model, for each newly declared product, the classifier can calculate the vector based on the commodity description and then compare it with vectors in the table to find similarities. Then it decides on the nearest HS code in the table and suggessts it to the importer. 
The solution uses two data sources: a pre-trained Word2Vector model provided by Google and a dataset containing product descriptions with HS codes from past customs declarations. 
:  
[GoogleNews-vectors-negative300.bin](https://www.kaggle.com/sandreds/googlenewsvectorsnegative300).
If you need to resize images, you have to use an HTML tag, like this:
<img src="https://github.com/vladlents/commodity-classifier/blob/main/HS-code-desc-example.png" width="400">
Where does your data come from? Do you collect it yourself or do you use data collected by someone else?
If you need to use links, here's an example:
[Twitter API](https://developer.twitter.com/en/docs)

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |

Below is a snapshot of a typical historical data set available from a customs statistics database that stores declaration level data. This is raw data that, once cleaned, can be used as a source to train the model.   
![HS_codes](https://github.com/vladlents/commodity-classifier/blob/main/HS-code-desc-example.png)

## Challenges

What does your project _not_ solve? Which limitations and ethical considerations should be taken into account when deploying a solution like this?

This case is limited to product descriptions coming in Enlish language but the same principle can work for other languages. 

## What next?

How could your project grow and become something even more? What kind of skills, what kind of assistance would you  need to move on? 


## Acknowledgments

* list here the sources of inspiration 
* do not use code, images, data etc. from others without permission
* when you have permission to use other people's materials, always mention the original creator and the open source / Creative Commons licence they've used
  <br>For example: [Sleeping Cat on Her Back by Umberto Salvagnin](https://commons.wikimedia.org/wiki/File:Sleeping_cat_on_her_back.jpg#filelinks) / [CC BY 2.0](https://creativecommons.org/licenses/by/2.0)
* etc
