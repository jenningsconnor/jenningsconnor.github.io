# Analyzing Hospital Stay Legnths

A brief note; this project will be a bit different than some of my others. Nevertheless, I put this here to showcase not only my ability to work with a limited dataset but to show how we can improve what data we have. 

> Project Overview

Given the impact of the Covid-19 pandemic and the challenges it has presented the American people, it's important to evaluate how we can improve our healthcare systems. This inspired me to work on a data project related to healthcare. To be precise, I wanted to work on a SQL-based data project given the demand for analysts fluent in SQL in healthcare. A colleague of mine directed me to a data set with the goal being to determine what factors play a role in increasing a patient's length of stay at a hospital. After an initial scan of the data, I downloaded the set with the goal being to transform the data set and derive as many insights as I can from it.

> Methodology

I used my own MySQL for the bulk of the exploration and transformation of the data. All code can be found [here](https://github.com/jenningsconnor/hospitalstayanalysis/blob/main/rawcode) (there's also a repository link at the end of this document). Once I uploaded the data into MySQL, I did a quick examination to see what the data showed. I immediately noticed a somewhat large red flag; stay lengths are divided into ranges (0-10, 11-20, 21-30, etc.), making what could be a numerical variable a categorical one. As soon as I saw this, I had to change my approach completely. I could no longer calculate average stay length based on various factors combining together (age range, hospital, patient's city, number of extra rooms available). Instead, I decided to transform the data so that cases would be group by a given category and then have the stay length as a subcategroy further dividing the data. Essentially, my output for my code looked like this:

<br>

![code_hosp_stay](code_example.png)

<br>

Though I could have created a regression equation by changing all the categories into numerical values, I decided against this. Part of this, admittedly, was because I wanted to use SQL for a project and not rely on Python. However, I also believe given the limits of this dataset it would be best to keep it as is and count up the raw numbers of cases divided by their respective categories. Not only would this allow someone to determine the percentages of which cases fall into a given category, it would also allow someone to see which percentage of cases within each category have higher or lower stay lengths.  

Another interesting thing to note about this dataset; case ID and patient ID are both present. Given this, for most of my exploration I decided to count both the number of patients and the number of cases per each grouping I created. 

> Key insights

I'd like to focus on what isn't present in the dataset: patient biometrics and demographics. Right off the bat, any results that can be gleaned from this data set will be somewhat limited. Sure, insights can be drawn, but anyone working in healthcare would argue biometrics and demographics are arguably essential. Alongside this, there's no information included with the data that shows which city codes belong to which city or which hospital codes belong to which hospital - meaning no demographics can be assumed from the population near a hospital. 

Another stumbling block is that age itself is a categorical range, with patients grouped into intervals of 10 (0-10, 11-20, 21-30, etc). This is arguably the most reckless categorization within the data set. Caring for a one year old patient is vastly different than caring for an eight year old patient, and caring for an adolescent pre-puberty can be wildly different than a ninteen year old adult. In order for relevant insight to be derived from this data, the owner of the data must provide accurate ages and not just a range. 

All of that said, none of this indicates that the data is completely useless or doesn't paint any sort of picture. If one were to display the data as a whole and only group cases by stay length, the data would appear skewed to the right. This means most of the cases are to the lower end as far as stay length. Most of the cases withint the data set have a stay length of either 11-20 or 21-30 days. When regrouping down the data into its respective subgroups (stay and age, stay and number of extra rooms, stay and hospital codes, etc), this trend holds up throughout most categories. This could indicate that there isn't an outlying variable that could somehow cause patients to become more likely to have a vastly increased stay range. However, there could be changes that occur on a level the data simply isn't capable of displaying due to the limits stay length being a range and not an integer.

> Links

[GitHub Repository](https://github.com/jenningsconnor/hospitalstayanalysis) <br>
[Kaggle Dataset](https://www.kaggle.com/nehaprabhavalkar/av-healthcare-analytics-ii)
