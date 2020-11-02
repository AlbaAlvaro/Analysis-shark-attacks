# Pandas project


## Importing of the data

For this project I used the python libraries Pandas, Matplotlib and Seaborn. First, I downloaded the file from the URL given and I moved it to the folder where I had the file I was working with in Jupyter Notebook and this README.md. 

To import the data into Jupyter Notebook I read the csv file with Pandas and I added the encoding because I couldn't read the file. This encoding defines ways to represent text characters in the latin alphabet.

```python
df = pd.read_csv("attacks.csv", encoding='latin-1')
```

### Showing the general information of the DataFrame

Before cleaning the DataFrame I extracted the general information such as the number of rows and columns, the name of each column and the data types in each column. From this information I observed several things:

- There are two columns ("Case Number.1" and "Case Number.2") that have the same name as Case Number, maybe they have the same information

- Other two columns ("href" and "href formula") that may have similar data

- Two columns called "Unnamed" 

- There are a lot of rows which have all null data

## Cleaning of the DataFrame

First of all, I examined the data related to the previous observations, and then I revised each column to see if the data should be cleaned.

I started with the Year column where I wanted to replace the values that were 0 with the values from the Data column on those rows. Finally, I decided not to replace them because if I did it I could not work with this column afterwards in the hypothesis.

Then, I revised the Case Number columns, as there were three columns with a similar name I checked whether the columns contained the same information and as they were not equal I revised ho many entries were different from the other columns in each of them. As a result, I found that there were few entries that were different in between these columns so I deleted the columns "Case Number.1" and "Case Number.2".

Next, I checked the columns "href" and "href formula" to see if they had the same information or if there were only a few entries different in between the two. As I found this to be true, I deleted the column href formula in order not to have duplicates.

Moreover, I revised the columns and rows with null information. I noticed that the two columns called "Unnamed" had most of their values null so I erased this two columns as they do not give significant information as well as the columns "Time" and "Age". The rows that had all null entries were also eliminated.

Then, I took a look at the column "Type" and I observed that there were three names that stand for the same type of attack, so I merged all in one name. 

I also revised the column "Country", there is no need of cleaning in this column as well as the column "Activity".

Then, I moved to the columns "Name" and "Sex", I observed that there were several entries in the "Name" column that belong to the "Sex" column so I first checked if the entries in both columns matched and as I could not be sure by only seen a feww entries I made the data in "Sex" be the same that the data in "Name". I also realized the "Sex" column had an empty space at the end of its name, so I deleted it.

Next, I checked the fatal column, there were values refering to the same but because of the way they were written they were not recognized as the same, so I replaced them by their true values, and also replace the NaN values by UNKNOWN. I also found that there was a confusing value in this column that had the structure of a year but it did not match the year of the entry where this attack was, so I revised the other data in the column and I found out that the attack was not fatal so I changed the entry for "N".

Finally, in the "Species" column I only changed its name as there was also an empty space at the end.

## Manipulation of the DataFrame

The manipulation of the DataFrame was developed to confirm or refute three hypothesis: the first one was that there are less fatal attacks due to surfing than to fishing, although the number of total attacks is higher in surfing, this could be due to the fact that when fishermen are fishing are disturbing the environment of the fish including sharks, but while surfing the human is not disturbing their habitat. The second one was that the number of attacks increases with the years but there are less fatal attacks nowadays.; and the third one was that there are more attacks on the coast facing the Pacific Ocean in Australia.

For the first hypothesis, I checked the number of attacks while surfing and while fishing, the number was higher while surfing. I also plotted a graph to show whether the majority of the attacks are fatal or not, as a result I obtained that the majority were non fatal attacks.


![fatals](C:\Users\34676\Pictures\fatals.png)


Then, I revised the number of fatal attacks while surfing and while fishing. For plotting this information I had some trouble. I first tried to plot the data by getting the percentage of fatals and non fatals of each activity but it did not came out, then I tried to do it by the Pandas function crosstab but I realized I had to extract the data from the original DataFrame in order to use it. I tried to make a new DataFrame by multiindexing, but I did not understand very well how it was done, and finally I arrived to the solution, I created two new DataFrames excluding all the activities that were not surfing or fishing from the previous DataFrame and I concateneted them in order to have a DataFrame with only these two activities. Then with Pandas crosstab I created a new table with the information on the activity and whether the attacks were fatal or not and from this table I created the bar plot, with the percentage of fatals and non fatals in each activity.


![fatals_activity](C:\Users\34676\Pictures\fatals_act)


For the second hypothesis, I created a new set of data without the years that were below 1500 as the other years were 0 in the DataFrame. Then, I plotted a graph showing the attacks each 20 years, depending on if they were fatal or not.

![attacks_fatal](C:\Users\34676\Pictures\year_fatal)

Finally, for the third hypothesis, I counted the attacks on each area of Australia, and I protted a graph showing them.

![australia_attacks](C:\Users\34676\Pictures\australis_attacks)

## Exporting of the DataFrame

For exporting the new set of data I created a new file named "attacks_clean.csv" and I exported the data with this command.
```python

df_clean.to_csv("attacks_clean.csv")

```
## Results, obstacles encountered, and lessons learned

As a result of the first hypothesis I obtained a cleaner DataFrame than the original one, and the result of the hypothesis was that there are more fatal attacks while fishing than when surfing. 

As a result of the ssecond hypothesis I obtained that The number of attacks increases with the years, with the highest increase from the year 2000 on. However, the number of fatal attacks keeps almost constant with the years, being the majority of the attacks from the year 1950 on non fatal.

I found it difficult to start cleaning the DataFrame as I did not know from where to start, but finally I made a checklist and I followed those points to get the data clean. In addition, it was also difficult for me to plot the last graph as I could not plot the data from the original DataFrame but I had to create a new one. With this project I have learned how to clean a set of data and some of the operations to get the results, as well as the plotting of the data.