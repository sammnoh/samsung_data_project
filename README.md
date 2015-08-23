First, I downloaded the zipfile in my working directory, after which I unzipped it, naming the unzipped file "Project3_unzipped" It was important to read the readMe and all the attached textfiles to get a grasp of how the data was structured. After familiarizing myself with the given files, "X_train.txt" & "X_test.txt" are the raw data measurements recorded by the Samsung gyroscope and accelerometer for all the movement types that could be recorded for all volunteer activities for all the volunteers in that pool.

Now, both records have the same number of variables since the movement types that could be measured are the same for both pools of volunteers. The only thing that would differ is in the number of rows becasuse each pool has a different number of volunteers participating (70% training, 30% testing)

Upon further investigation, one finds a file named "features.txt" that lists the name metric of each of the measurement. So I made sure to have that be the column names of the "X_train.txt" and "X_test.txt" files.

subject_train.txt & subject_test.txt are data frames that indicate the Volunteer ID#. I made sure to bind the 2 using rbind, making sure to keep the ordering of the argument consistent saving the full Volunteer ID# as "full_subjects"

y_train.txt & y_test.txt are data frames that indicate which 1 of the 6 activities the row is indicative of. I made sure to bind these two as well using rbind as full_activity

activity_labels.txt is a data frame that references what each activity number correlates to. I merged activity_labels with full_activity, which replaced the numeric index with its equivalent character activity.

Now that we have all the pieces together, I combined the full, full_subject and full_activity using cbind to get the full tidy data.

Next, I used full[,grepl("mean|std|SubjectID|Activity", colnames(full))] to give me the columns with mean or std (while keeping SubjectID & Activity

Lastly, I made a new table fulfilling the 5th requirement by way of data_average <- (full1 %>% group_by(SubjectID, Activity) %>% summarise_each(funs(mean))), which gives us the average of each activity for each activity per volunteer.
