STUDY DESIGN
============

This wearable computing data was derived from the Samsung Galazy S smartphone and futher
colsolidated into a series of statistical measurements.  The purpose of this study was
foremost to consolidate the mean and standard deviations as derived from these raw data
sets and to further summarize this data into a list of human-readable measurements.
The final output consisting of a row for each measurement and a column for each subject
and activity pair, the value of which is the mean of those measurements.

SOURCE
------
The source of the RAW data can be found at:

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

This data was extracted into cloudfront.net for this coursera class located at:

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

and a copy of that has been packaged along with this package in the file:

proj_dat.zip

EXCLUSIONS
----------

* **Inertial Signals** - is the raw data before the initial consolidation, it wasn't
required to calculate our means

* columns from *X_train.txt* and *X_test.txt* that did not include the mean() or
std() values.

REQUIRED FILES
--------------
* **activity_labels.txt** - displays a list of the activities and the numerical value they
are associated with.
* **features.txt** - contains coded values of the measurements that were taken.
* **test/X_test.txt** - the actual numerical values of the given measurements for the test suite
* **test/y_test.txt** - the categorical interger for associating the activity with the measurement
* **test/subject_test.txt** - the number of the test volunteer
* **train/X_train.txt** - the actual numerical values of the given measurements for the training suite
* **train/y_train.txt** - the categorical interger for associating the activity with the measurement
* **train/subject_train.txt** - the number of the test volunteer

CODE BOOK
=========

VARIABLES
---------

The data contains the mean of 3-axial linear acceleration and 3-axial angular velocities
at a constant rate of 50Hz as derived from a Samsung Galaxy S smartphone worn on the hip
during different activities by 30 ~~victims~~ volunteers.

SUMMARY CHOICES
---------------

The data excluded everything but the mean or standard deviation columns which resulted
in the following (66) row.names:

* Fast Fourier Transform Body Acceleration Mean X 
* Fast Fourier Transform Body Acceleration Mean Y 
* Fast Fourier Transform Body Acceleration Mean Z 
* Fast Fourier Transform Body Acceleration Standard Deviation X 
* Fast Fourier Transform Body Acceleration Standard Deviation Y 
* Fast Fourier Transform Body Acceleration Standard Deviation Z 
* Fast Fourier Transform Body Acceleration Jerk Signal Mean X 
* Fast Fourier Transform Body Acceleration Jerk Signal Mean Y 
* Fast Fourier Transform Body Acceleration Jerk Signal Mean Z 
* Fast Fourier Transform Body Acceleration Jerk Signal Standard Deviation X 
* Fast Fourier Transform Body Acceleration Jerk Signal Standard Deviation Y 
* Fast Fourier Transform Body Acceleration Jerk Signal Standard Deviation Z 
* Fast Fourier Transform Body Acceleration Euclidean Norm Mean 
* Fast Fourier Transform Body Acceleration Euclidean Norm Standard Deviation 
* Fast Fourier Transform Body Body Acceleration Jerk Signal Euclidean Norm Mean 
* Fast Fourier Transform Body Body Acceleration Jerk Signal Euclidean Norm Standard Deviation 
* Fast Fourier Transform Body Body Gyro Jerk Signal Euclidean Norm Mean 
* Fast Fourier Transform Body Body Gyro Jerk Signal Euclidean Norm Standard Deviation 
* Fast Fourier Transform Body Body Gyro Euclidean Norm Mean 
* Fast Fourier Transform Body Body Gyro Euclidean Norm Standard Deviation 
* Fast Fourier Transform Body Gyro Mean X 
* Fast Fourier Transform Body Gyro Mean Y 
* Fast Fourier Transform Body Gyro Mean Z 
* Fast Fourier Transform Body Gyro Standard Deviation X 
* Fast Fourier Transform Body Gyro Standard Deviation Y 
* Fast Fourier Transform Body Gyro Standard Deviation Z 
* Time Domain Body Acceleration Mean X 
* Time Domain Body Acceleration Mean Y 
* Time Domain Body Acceleration Mean Z 
* Time Domain Body Acceleration Standard Deviation X 
* Time Domain Body Acceleration Standard Deviation Y 
* Time Domain Body Acceleration Standard Deviation Z 
* Time Domain Body Acceleration Jerk Signal Mean X 
* Time Domain Body Acceleration Jerk Signal Mean Y 
* Time Domain Body Acceleration Jerk Signal Mean Z 
* Time Domain Body Acceleration Jerk Signal Standard Deviation X 
* Time Domain Body Acceleration Jerk Signal Standard Deviation Y 
* Time Domain Body Acceleration Jerk Signal Standard Deviation Z 
* Time Domain Body Acceleration Jerk Signal Euclidean Norm Mean 
* Time Domain Body Acceleration Jerk Signal Euclidean Norm Standard Deviation 
* Time Domain Body Acceleration Euclidean Norm Mean 
* Time Domain Body Acceleration Euclidean Norm Standard Deviation 
* Time Domain Body Gyro Mean X 
* Time Domain Body Gyro Mean Y 
* Time Domain Body Gyro Mean Z 
* Time Domain Body Gyro Standard Deviation X 
* Time Domain Body Gyro Standard Deviation Y 
* Time Domain Body Gyro Standard Deviation Z 
* Time Domain Body Gyro Jerk Signal Mean X 
* Time Domain Body Gyro Jerk Signal Mean Y 
* Time Domain Body Gyro Jerk Signal Mean Z 
* Time Domain Body Gyro Jerk Signal Standard Deviation X 
* Time Domain Body Gyro Jerk Signal Standard Deviation Y 
* Time Domain Body Gyro Jerk Signal Standard Deviation Z 
* Time Domain Body Gyro Jerk Signal Euclidean Norm Mean 
* Time Domain Body Gyro Jerk Signal Euclidean Norm Standard Deviation 
* Time Domain Body Gyro Euclidean Norm Mean 
* Time Domain Body Gyro Euclidean Norm Standard Deviation 
* Time Domain Gravity Acceleration Mean X 
* Time Domain Gravity Acceleration Mean Y 
* Time Domain Gravity Acceleration Mean Z 
* Time Domain Gravity Acceleration Standard Deviation X 
* Time Domain Gravity Acceleration Standard Deviation Y 
* Time Domain Gravity Acceleration Standard Deviation Z 
* Time Domain Gravity Acceleration Euclidean Norm Mean 
* Time Domain Gravity Acceleration Euclidean Norm Standard Deviation 

This was further broken down by subject (of which there were 30) and
activity (6) which consisted of:

* WALKING
* WALKING UPSTAIRS
* WALKING DOWNSTAIRS
* SITTING
* STANDING
* LAYING

Resulting in a total of 180 (30*6) columns.
30 Volunteers with 6 activities each.

EXPERIMENTAL STUDY DESIGN
-------------------------

The result is a summary of the data which displays averages for the mean and standard
deviation of each measurement by activity and test subject.

**No other data was harmed (used) in the processing of this data.**

RESULTING DATASET
-----------------

A single table is returned with...

* Each Column is a measure of one Subject.Activity pair
* Each Observation is contained on it's own row
* Header Row Contains the Column names
* Variable Names are Human Readable

INSTRUCTION LIST
================

INPUT
-----
Though their are no parameters for this library the directory structure must be setup
appropriately to read in the raw data. see the README.md file bundled with this file
if you have questions as to how to setup your directory structure.

OUTPUT
------
data.frame consisting of the tidy data set.

DETAILED PROGRAMMING PROCEEDURE
-------------------------------
1. Initialized with test data using subject, activity and readings to create a data.frame

2. Merged training subject, activity and readings data into this data.frame

3. Added Column Names from features.txt file

4. Extracted subject, activity and only the measurements for the mean and standard deviation
into our current dataset

5. Used descriptive activity names to rename the numerical activities from activity_labels.txt

6. Appropriately label'd the data set with descriptive column names, using a search/replace
mechanism with the following ruleset:

    * begins with 't' -> Time Domain
    * begins with 'f' -> Fast Fourier Transform
    * Acc -> Acceleration
    * Jerk -> Jerk Signal
    * Mag -> Euclidean Norm
    * -mean() -> Mean
    * -std() -> Standard Deviation
    * dash followed by UPPER CASE character -> remove the dash
    * a lower case character followed by an UPPER CASE character -> insert a space between them 
    and re-ran the last rule twice to ensure "BodyBodyGuru" was separated twice

**OUTPUT** return a second, independent tidy data set with the average of each variable for each
activity by each subject

SAMPLE OUTPUT
-------------

```
> UCIdata <- run_analysis()
> UCIdata[1:4,1:4]
```

|                                                             |  1.WALKING|   2.WALKING|   3.WALKING| 4.WALKING|
|-------------------------------------------------------------|----------:|-----------:|-----------:|---------:|
|Fast Fourier Transform Body Acceleration Mean X              |-0.06810286| 0.084727087|-0.138107866| 0.1277641|
|Fast Fourier Transform Body Acceleration Mean Y              |-0.97660964|-0.972693201|-0.977771591|-0.9838265|
|Fast Fourier Transform Body Acceleration Mean Z              |-0.97130596|-0.972116880|-0.962355639|-0.9679632|
|Fast Fourier Transform Body Acceleration Standard Deviation X|-0.14176147| 0.004590468|-0.007358565|-0.4903719|

