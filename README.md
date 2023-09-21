<!-- This is the markdown template for the final project of the Building AI course, 
created by Reaktor Innovations and University of Helsinki. 
Copy the template, paste it to your GitHub README and edit! -->

# Project Title: Commodity code-classifier

Final project for the Building AI course

## Summary
# Describe briefly in 2-3 sentences what your project is about. About 250 characters is a nice length! 
The project is about building a commodity classifier that will help assess the correctness of the declared HS code upon import into the country. The classifier is trained to predict the HS code using historical data about previously declared products. For each new declaration, it can predict the HS code based on product description and then compare it with the declared one. 

## Background

# Which problems does your idea solve? How common or frequent is this problem? What is your personal motivation? Why is this topic important or interesting?

The idea can help in solving multiple problems arising in relation to the importation of goods, in particular:
* it can help prevent deliberate fraud on imported goods;
* identify misdeclared goods due to unintended errors;
* help importers in selecting correct product group, that is HS code, from the the Harmonized System (HS) while declaring goods. 

## How is it used?
# Describe the process of using the solution. In what kind situations is the solution needed (environment, time, etc.)? Who are the users, what kinds of needs should be taken into account?

The solution can be used by customs officers to evaluate the correctness of the declared HS code on a new incoming declaration using the textual description of goods provided by the importer. Since the HS code is is used for customs duty calculation, it is important to have HS code consistent with the goods description. For simplicity, the solution uses a pre-trained Word2Vector model provided by Google, which is further trained using goods descriptions from historical customs declarations. Then the trained model is used for evaluating the correctness of the declared HS code in every new declaration.    

To translate the product description (free-text sentence) into a vector, the classifier will use a pre-trained embedding model provided by Google: GoogleNews-vectors-negative300.bin (https://www.kaggle.com/sandreds/googlenewsvectorsnegative300). With this word to vector (Word2Vector) model, the classifier can calculate the HS code based on the commodity description and then compare it with the declared HS.

Images will make your README look nice!
Once you upload an image to your repository, you can link link to it like this (replace the URL with file path, if you've uploaded an image to Github.)
![Cat](https://upload.wikimedia.org/wikipedia/commons/5/5e/Sleeping_cat_on_her_back.jpg)

If you need to resize images, you have to use an HTML tag, like this:
<img src="https://upload.wikimedia.org/wikipedia/commons/5/5e/Sleeping_cat_on_her_back.jpg" width="300">

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
Where does your data come from? Do you collect it yourself or do you use data collected by someone else?
If you need to use links, here's an example:
[Twitter API](https://developer.twitter.com/en/docs)

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |

## Challenges

What does your project _not_ solve? Which limitations and ethical considerations should be taken into account when deploying a solution like this?

## What next?

How could your project grow and become something even more? What kind of skills, what kind of assistance would you  need to move on? 


## Acknowledgments

* list here the sources of inspiration 
* do not use code, images, data etc. from others without permission
* when you have permission to use other people's materials, always mention the original creator and the open source / Creative Commons licence they've used
  <br>For example: [Sleeping Cat on Her Back by Umberto Salvagnin](https://commons.wikimedia.org/wiki/File:Sleeping_cat_on_her_back.jpg#filelinks) / [CC BY 2.0](https://creativecommons.org/licenses/by/2.0)
* etc
