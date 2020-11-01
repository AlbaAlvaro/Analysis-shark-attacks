# Pandas project

detailed explanation of the process followed in the importing, cleaning, manipulation, and exporting of your data as well as your results, obstacles encountered, and lessons learned

## Importing of the data

For this project I used the python libraries Pandas, Matplotlib and Seaborn. First, I downloaded the file from the URL given and I moved it to the folder where I had the file I was working with in Jupyter Notebook and this README.md. 

To import the data into Jupyter Notebook I read the csv file with Pandas and I added the encoding because I couldn't read the file. This encoding defines ways to represent text characters in the latin alphabet.

### Showing the general information of the DataFrame

Before cleaning the DataFrame I extracted the general information such as the number of rows and columns, the name of each column and the data types in each column. From this information I observed several things:

- There are two columns (Case Number.1 and Case Number.2) that have the same name as Case Number, maybe they have the same information

- Other two columns (href and href formula) that may have similar data

- Two columns called Unnamed 

- There are a lot of rows which have all null data

## Cleaning of the DataFrame

First of all, I examined the data related to the previous observations, and then I revised each column to see if the data should be cleaned.

I started with the Case Number columns, as there were three columns with a similar name I checked whether the columns contained the same information and as they were not equal I revised ho many entries were different from the other columns in each of them. As a result, I found that there were few entries that were different in between these columns so I deleted the columns "Case Number.1" and "Case Number.2".

Next, I checked the columns "href" and "href formula" to see if they had the same information or if there were only a few entries different in between the two. As I found this to be true, I deleted the column href formula in order not to have duplicates.

Moreover, I revised the columns and rows with null information. I noticed that the two columns called "Unnamed" had most of their values null so I erased this two columns as they do not give significant information. The rows that had all null entries were also eliminated.

Then, I took a look at the column "Type" and I observed that there were three names that stand for the same type of attack, so I merged all in one name. 

I also revised the column "Country", there is no need of cleaning in this column as well as the column "Activity".

Then, I moved to the columns "Name" and "Sex", I observed that there were several entries in the "Name" column that belong to the "Sex" column so I first checked if the entries in both columns matched and as I could not be sure by only seen a feww entries I made the data in "Sex" be the same that the data in "Name". I also realized the "Sex" column had an empty space at the end of its name, so I deleted it.

Next, I checked the fatal column, there were values refering to the same but because of the way they were written they were not recognized as the same, so I replaced them by their true values, and also replace the NaN values by UNKNOWN. I also found that there was a confusing value in this column that had the structure of a year but it did not match the year of the entry where this attack was.

Finally, in the "Species" column I only changed its name as there was also an empty space at the end.

## Manipulation of the DataFrame

The manipulation of the DataFrame was developed to confirm or refute the hypothesis that there are less fatal attacks due to surfing than to fishing, although the number of total attacks is higher in surfing. This could be due to the fact that when fishermen are fishing are disturbing the environment of the fish including sharks, but while surfing the human is not disturbing their habitat.

First, I checked the number of attacks while surfing and while fishing, the number was higher while surfing. I also plotted a graph to show whether the majority of the attacks are fatal or not, as a result I obtained that the majority were not fatal attacks.

grafico
![fatals](C:\Users\34676\Pictures)


Then, I revised the number of fatal attacks while surfing and while fishing. For plotting this information I had some trouble. I first tried to plot the data by getting the percentage of fatals and non fatals of each activity but it did not came out, then I tried to do it by the Pandas function crosstab but I realized I had to extract the data from the original DataFrame in order to use it. I tried to make a new DataFrame by multiindexing, but I did not understand very well how it was done, and finally I arrived to the solution, I created two new DataFrames excluding all the activities that were not surfing or fishing from the previous DataFrame and I concateneted them in order to have a DataFrame with only these two activities. Then with Pandas crosstab I created a new table with the information on the activity and whether the attacks were fatal or not and from this table I created the bar plot, with the percentage of fatals and non fatals in each activity.

tabla y grafico


## Exporting of the DataFrame

For exporting the new set of data I df_clean.to_csv("attacks_clean.csv")