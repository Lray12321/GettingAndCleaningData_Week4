variables: 


features_list - read features.txt

activity - read activity_labels.txt

subjectTest - read subject_test.txt

xTest - read X_test.txt

yTest - readt Y_test.txt

yTestLabel - combined files of yTest and activity

testData - combined files of subjectTest, yTestLabel and xTest

subjectTrain - read subject_train.txt

xTrain - read X_train.txt

yTrain - read Y_train.txt

yTrainLabel - combined files of yTrain and activity

trainData - combined files of subjectTrain, yTrainLabel, xTrain

allData -combined files of testData and trainData

Measurements - the standard deviation and mean of allData

tidyData - tidy data of measurements based on subject and activity
  



Functions: 



read.table() - ability to read the data of text document

cbind() - combine multiple data sets into one

left_join() - merge two datasets where the merge matches rows from the first column to the second column

rbind() - combined vectors by row

group_by() - group variables together

summarise_each() - summarize data sets by certain function

write.table() - create a new .txt of dataset

