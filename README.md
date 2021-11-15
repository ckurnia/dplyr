# dplyr
Week 4 Activity: dplyr
#Use a dataset from Base R, HairEyeColor
#and give it a new name
students<-data.frame(HairEyeColor)

#See the top rows of the data
#TASK: replace the ? with the function
head(students)

#Install and call the package dplyr
#TASK: replace the ? with the function
install.packages("dplyr")
library(dplyr)

#Let's just see the hair and sex columns
select(students, Hair, Sex)

#Let's name the dataset with just the two columns, Hair and Sex
#TASK: replace the ?s with the column names
hairsex<-select(students, Hair, Sex)

#Let's get rid of the Sex column in the hairsex dataset
#TASK: replace the ? with the dataset name
justhair<-select(hairsex,-Sex)

#Let's rename a column name
#TASK: replace the ? with the column name
rename(students, gender=Sex)

#Let's make a new dataset with the new column name
#TASK: replace the ? with the function 
students1<-transform(students, gender=Sex)

#Let's filter just the males from our dataset
#TASK: replace the ? with the dataset name
males<-filter(students1, gender=="Male")

#Let's arrange our data by frequency
#TASK: replace the ? with the dataset name
arrange(students1, Freq)

#Let's group our data by gender (or Sex)
#TASK: replace the ? with the dataset and column name
group_by(students1, Sex)

#Let's see how many students were examined in the dataset (total the frequency)
total=mutate(students, total=cumsum(Freq))
#See the total of the cumulative frequency
tail(total, 1)
#Or I could have just done:
sum(students$Freq)
#TASK: Comment with the total (sum) here: 592

#Since we have a males dataset, let's make a females dataset
#TASK: replace the ? with the column name
females<-filter(students1, gender=="Female")

#And now let's join the males and females
#TASK: replace the ?s with the column names
union(males,females)

#Or this way
#TASK: replace the ?s with the column names
newset<-bind_rows(males,females)

#Optional Task: add any of the other functions 
#you learned about from the dplyr package
