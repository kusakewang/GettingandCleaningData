Introduction
------------------------------
Dataset `data_tidy.txt` is created by running `run_analysis.R'.

* Firstly, all the files needed are read into R. To merge the training and testing data, first, combind `Xtrain`, `sub_train` which contains subjectID, and 'ytrain' by comumn to form training dataset. Do the same to form the testing dataset. Then combind  of those two sets by row. 

Data and Variables Descriptions
------------------------------
* For the final dataset `data_tidy.txt`, there are 180 observations with 66 selected features as well as "ActivityName" and "SubjectID".
  The names of variables are listed below
  
```r
names(data_tidy)
```

```
 [1] "ActivityName"            "SubjectID"               "tBodyAcc-mean()-X"      
 [4] "tBodyAcc-mean()-Y"       "tBodyAcc-mean()-Z"       "tBodyAcc-std()-X"       
 [7] "tBodyAcc-std()-Y"        "tBodyAcc-std()-Z"        "tGravityAcc-mean()-X"   
[10] "tGravityAcc-mean()-Y"    "tGravityAcc-mean()-Z"    "tGravityAcc-std()-X"    
[13] "tGravityAcc-std()-Y"     "tGravityAcc-std()-Z"     "tBodyAccJerk-mean()-X"  
[16] "tBodyAccJerk-mean()-Y"   "tBodyAccJerk-mean()-Z"   "tBodyAccJerk-std()-X"   
[19] "tBodyAccJerk-std()-Y"    "tBodyAccJerk-std()-Z"    "tBodyGyro-mean()-X"     
[22] "tBodyGyro-mean()-Y"      "tBodyGyro-mean()-Z"      "tBodyGyro-std()-X"      
[25] "tBodyGyro-std()-Y"       "tBodyGyro-std()-Z"       "tBodyGyroJerk-mean()-X" 
[28] "tBodyGyroJerk-mean()-Y"  "tBodyGyroJerk-mean()-Z"  "tBodyGyroJerk-std()-X"  
[31] "tBodyGyroJerk-std()-Y"   "tBodyGyroJerk-std()-Z"   "tBodyAccMag-mean()"     
[34] "tBodyAccMag-std()"       "tGravityAccMag-mean()"   "tGravityAccMag-std()"   
[37] "tBodyAccJerkMag-mean()"  "tBodyAccJerkMag-std()"   "tBodyGyroMag-mean()"    
[40] "tBodyGyroMag-std()"      "tBodyGyroJerkMag-mean()" "tBodyGyroJerkMag-std()" 
[43] "fBodyAcc-mean()-X"       "fBodyAcc-mean()-Y"       "fBodyAcc-mean()-Z"      
[46] "fBodyAcc-std()-X"        "fBodyAcc-std()-Y"        "fBodyAcc-std()-Z"       
[49] "fBodyAccJerk-mean()-X"   "fBodyAccJerk-mean()-Y"   "fBodyAccJerk-mean()-Z"  
[52] "fBodyAccJerk-std()-X"    "fBodyAccJerk-std()-Y"    "fBodyAccJerk-std()-Z"   
[55] "fBodyGyro-mean()-X"      "fBodyGyro-mean()-Y"      "fBodyGyro-mean()-Z"     
[58] "fBodyGyro-std()-X"       "fBodyGyro-std()-Y"       "fBodyGyro-std()-Z"      
[61] "fBodyAccMag-mean()"      "fBodyAccMag-std()"       "fBodyAccJerkMag-mean()" 
[64] "fBodyAccJerkMag-std()"   "fBodyGyroMag-mean()"     "fBodyGyroMag-std()"     
[67] "fBodyGyroJerkMag-mean()" "fBodyGyroJerkMag-std()" 
```
Variable name    | Description
-----------------|------------
subjectID         | ID the subject who performed the activity for each window sample. Its range is from 1 to 30.
ActivityName      | Activity name

The description of other features can be found in `features_info.txt`
