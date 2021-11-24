sapply(packages, require, character.only=TRUE, quietly=TRUE)
path <- getwd()
url <- "https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"
download.file(url, file.path(path, "dataFiles.zip"))
unzip(zipfile = "dataFiles.zip")


features_list <- read.table("features.txt", col.names = c("no","features"))
activity <- read.table("activity_labels.txt", col.names = c("label", "activity"))


# Read test dataset 
subjectTest <- read.table("test/subject_test.txt", col.names = "subject")
xTest <- read.table("test/X_test.txt", col.names = features_list$features)
yTest <- read.table("test/Y_test.txt", col.names = "label")
yTestLabel <- left_join(yTest, activity, by = "label")

testData <- cbind(subjectTest, yTestLabel, xTest)
testData <- select(testData, -label)


# Read train dataset
subjectTrain <- read.table("train/subject_train.txt", col.names = "subject")
xTrain <- read.table("train/X_train.txt", col.names = features_list$features)
yTrain <- read.table("train/Y_train.txt", col.names = "label")
yTrainLabel <- left_join(yTrain, activity, by = "label")

trainData <- cbind(subjectTrain, yTrainLabel, xTrain)
trainData <- select(trainData, -label)

# combine test and train data set
allData <- rbind(testData, trainData)

# Get mean and standard deviation
Measurements <- select(allData, contains("mean"), contains("std"))

# Average of each group

Measurements$subject <- as.factor(allData$subject)
Measurements$activity <- as.factor(allData$activity)

tidyData <- Measurements %>%
  group_by(subject, activity) %>%
  summarise_each(funs(mean))
  

write.table(tidyData, "tidy_data_set.txt", row.name=FALSE)

 
