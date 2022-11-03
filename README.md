# Wafer-Fault-Detection

Developed classification model to classify wafer sensors need to be replaced based on quality and increased productivity by 24%.


##Architecture 
 
<img width="1012" alt="Screen Shot 2022-11-03 at 11 02 50 AM" src="https://user-images.githubusercontent.com/68578215/199799978-b3b4547b-a3ee-4539-b426-3bce9e273524.png">



## Problem Statement

The inputs of various sensors for different wafers have been provided. In electronics, a wafer (also called a slice or substrate) is a thin slice of semiconductor used for the fabrication of integrated circuits. The goal is to build a machine learning model which predicts whether a wafer needs to be replaced or not(i.e., whether it is working or not) based on the inputs from various sensors. There are two classes: +1 and -1.

- +1 means that the wafer is in a working condition and it doesn’t need to be replaced.
- -1 means that the wafer is faulty and it needs to be replaced.

## Data Type

- The data used for training consisted of 591 columns of float data type.
- And the data used Prediction consisted of 590 columns of float data type.


## Techniques used for Data Pre-Processing
- Null values are checked. If Null values are present, then they are imputed using KNN Imputer.
- Columns having zero standard deviation were removed, as they don’t give any information during model training.
- Unnecessary columns were removed during training like Wafer's name.

## 6.	Validation of Files

**Name Validation-** Validated the name of the files based on the given name in the schema file. We have created a regex pattern as per the name given in the schema file to use for validation. After validating the pattern in the name, we check for the length of date in the file name as well as the length of time in the file name. If all the values are as per requirement, we move such files to "Good_Data_Folder" else we move such files to "Bad_Data_Folder."

**Number of Columns-** Validate the number of columns present in the files, and if it doesn't            match with the value given in the schema file, then the file is moved to "Bad_Data_Folder."

**Name of Columns-** The name of the columns is validated and should be the same as given in the schema file. If not, then the file is moved to "Bad_Data_Folder".

**The datatype of columns-** The datatype of columns is given in the schema file. This is validated when we insert the files into Database. If the datatype is wrong, then the file is moved to "Bad_Data_Folder".

**Null values in columns-** If any of the columns in a file have all the values as NULL or missing, we discard such a file and move it to "Bad_Data_Folder".

Files from the "Bad_Data_Folder" are moved to “Archived Bad_Data_Folder” before deleting the "Bad_Data_Folder".

The “Archived_Bad_Data_Folder” is then sent to the client for rechecking.

"Good_Data_Folder" is also deleted to save memory.







## Functional Architecture
