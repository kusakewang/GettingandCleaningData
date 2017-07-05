### Getting and Cleaning Data Course Project ###

### This R code is for cleaning the given data


rm(list = ls())
library(data.table)
library(plyr)

## download and unzip data
fname <- "HAR.zip"

url <- "https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"

if (!file.exists(fname)) {
  download.file(url, destfile = fname)  
}

if (!file.exists("UCI HAR Dataset")) {
  unzip(fname)
}
## set working directory to the UCI HAR dataset

setwd("E:/open course/Data science specialization/UCI HAR Dataset")

## read in all the files
features <- read.table("features.txt")
features[, 2] <- as.character(features[, 2])
act_labels <- read.table("activity_labels.txt")
act_labels[, 2] <- as.character(act_labels[, 2])
Xtrain <- read.table("train/X_train.txt")
ytrain <- read.table("train/y_train.txt")
sub_train <- read.table("train/subject_train.txt")
Xtest <- read.table("test/X_test.txt")
ytest <- read.table("test/y_test.txt")
sub_test <- read.table("test/subject_test.txt")

##  1. Merges the training and the test sets to create one data set.

train <- cbind(Xtrain, sub_train, ytrain)
test <- cbind(Xtest, sub_test, ytest)
data_all <- rbind(train, test)
colnames(data_all) <- c(features[, 2], "SubjectID", "ActivityID")


# 2. Extracts only the measurements on the mean and standard deviation 
#    for each measurement.

featureselct <- features[grepl("mean\\(\\)|std\\(\\)", features[, 2]), 2]
data_subset <- data_all[, c(featureselct,"SubjectID", "ActivityID")]

# 3. Uses descriptive activity names to name the activities in the data set
#    Here a new column ActivityName is added to the dataset from step2 to 
#    identify the descriptive activity names

colnames(act_labels) <- c("ActivityID", "ActivityName")
data_subset$ActivityName <- act_labels$ActivityName[data_subset$ActivityID]
i <- match("ActivityID", names(data_subset))
data_subset <- data_subset[, -i]


# 4. Appropriately labels the data set with descriptive variable names
# notice some Body in the names of features are repeated, need to fix it

colnames(data_subset) <- gsub("[Bb]ody[Bb]ody","Body", colnames(data_subset))


# 5. From the data set in step 4, creates a second,independent tidy data set
#    with the average of each variable for each activity and each subject.

data_tidy <- ddply(data_subset, c("ActivityName", "SubjectID"), function(x) colMeans(x[, 1:66]))

write.table(data_tidy, "data_tidy.txt",row.name=FALSE)
