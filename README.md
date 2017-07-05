# Getting and Cleaning Data Course Project
According to the project requirements, by using the data from

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

I create a R script called run_analysis.R that does the following 5 steps.

1. Merges the training and the test sets to create one data set.
2. Extracts only the measurements on the mean and standard deviation for each measurement.
3. Uses descriptive activity names to name the activities in the data set
4. Appropriately labels the data set with descriptive variable names.
5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

# Files

This repository hosts the R code and documentation files for this project.

`run_analysis.R` contains all the code to perform the analyses required above. 

`CodeBook.md` describes the variables, the data, and any transformations or work that I performed to clean up the data.

`data_tidy.txt` is the tidy data I got from step 5 that described above
