
## Student Performance

### Data Summaries

![[Pasted image 20251127125533.png|400]]
Here's a correlation heatmap of all the variables. We can see that *study time* and *absences* have the largest correlations with G3 grades, while *age* has a large negative correlation with G2 grades.
#### Gender
![[Pasted image 20251125192043.png|400]]
Value counts:
- Men: 151
- Women: 149

Very even split, so the the data is well balanced across genders.

#### Age

**5 Number Summary:**

| Describers | Value |
| ---------- | ----- |
| Mean       | 18.59 |
| STD        | 2.396 |
| Minimum    | 15    |
| 25%        | 17    |
| 50%        | 18    |
| 75%        | 21    |
| Maximum    | 22    |
Looking at the bar plot, we can see that our samples are decently distributed, with a couple of hotspots at times. 
![[Pasted image 20251125193040.png|400]]

#### Study Time
**5 Number Summary:**

| Describer | Value |
| --------- | ----- |
| Mean      | 10.42 |
| STD       | 5.9   |
| Minimum   | 1     |
| 25%       | 5     |
| 50%       | 11    |
| 75%       | 16    |
| Maximum   | 20    |
![[Pasted image 20251125200202.png|400]]
Looking at the weekly study hours, we can see that there's a dip in the middle. There's also two large peaks at 5 hours a week and 12-13 hours a week. This indicates that there's a small U-shape to the distribution.

#### Failures
**5 Number Summary**

| Describer | Value |
| --------- | ----- |
| Mean      | 0.41  |
| STD       | 0.651 |
| Minimum   | 0     |
| 25%       | 0     |
| 50%       | 0     |
| 75%       | 1     |
| Maximum   | 3     |
![[Pasted image 20251125213621.png|400]]
We can see here that the data has a large skew towards students with no failed classes. However, since it's generally pretty hard to fail in high school, this is expected. This is especially notable when looking at the quartiles, as at least 50% of the samples have no previously failed classes.

#### Absences
**5 Number Summary**

| Describer | Value |
| --------- | ----- |
| Mean      | 5     |
| STD       | 2.27  |
| Minimum   | 0     |
| 25%       | 3     |
| 50%       | 5     |
| 75%       | 7     |
| Maximum   | 11    |

![[Pasted image 20251125214209.png|400]]
Looking at the data, we can see that there's a *normal distribution* of the data, with a distinctive bell-curve hump in the middle. This makes sense, as students might get sick, skip, or have emergencies that require an absence. However, it is important to note that there amore students over the average, compared to under the average. This can be seen with the histogram.

#### Grades
**5 Number Summary**

|         | G1    | G2   | G3    |
| ------- | ----- | ---- | ----- |
| Mean    | 10.18 | 9.83 | 10.29 |
| STD     | 6.21  | 6.1  | 5.94  |
| Minimum | 0     | 0    | 0     |
| 25%     | 4     | 4.75 | 5     |
| 50%     | 10    | 9    | 10    |
| 75%     | 16    | 15   | 15    |
| Maximum | 20    | 20   | 20    |
![[Pasted image 20251125215513.png|400]]
Looking at the data here, we can see that there is a slight dip in average grades during the second exam, with a big **lock in** during the final. It is important to note that the minimum and maximum grades are the same across the board. This shows that even with an increased average, students still fail on the final exam. 

### Final Grade Comparisons
When comparing the different columns, I found that the graphics were incomprehensible. However, after splitting the data into 3 different ranges, we can see that

#### Age Comparison
![[Pasted image 20251125221329.png|300]]![[Pasted image 20251125221504.png|300]]

Here we can see that both male and female final grades take a dip between ages 18 and 20. However, with the men they have a much large dip compared to the women. Yet, the women have a larger spread of grades in that same period, with inliers going much lower compared to the men (until they turn 21).

#### Study Time Comparison
![[Pasted image 20251125223456.png|300]]![[Pasted image 20251125223949.png|300]]
Here we can see a very big disparity between the genders when it comes to their relationship between their weekly study hours and their final exam grades. Women seem to do worse as their weekly study hours increase, while men are by comparison fairly stable in their grades despite the study hours. Funnily enough, for men the extremes perform a lot better than median.
#### Absences Comparison
![[Pasted image 20251125224916.png|300]]![[Pasted image 20251125224858.png|300]]
Here we can see that male grades decrease with the amount of absences (inverse relationship), while the female grades are relatively consistent even with absences. Men especially take a huge drop in final exam grades after 8 absences, while women actually have a higher mean final grade (compared to other women) with the same amount of absences.

### G1 -> G3 Grades
![[Pasted image 20251127113925.png|300]]![[Pasted image 20251127114022.png|300]]
Looking at the progression of grades for both male and female students, we can see that there's a small dip in the mean during G2 regardless of gender. When it comes to differences, females tend to have smaller variance compared to males over time.

### Conclusions
Looking at our data, we can grab a couple potential insights. The correlation heatmap shows that *study time*, *age*, and *absences* have the largest correlation with grades. It's important to note that there is only negative correlations.
However, these impact students differently, with *absences* strongly affecting males and *study time* strongly affecting females. Yet, it's safe to say that low to medium study hours and few absences lead to better grades. 
When it comes to student *age*, there is a clear decline in performance with aging. While there's not much you can do about the inevitable creep of time, educators could perhaps put more focus on older students. 

## Hospital Readmission

### Data Summary

#### Gender
![[Pasted image 20251128112423.png|300]]
Female    206
Male      194

We can see a very balanced gender ration, which is consistent the population (1/2). There are slightly more women than men though, but it's not significant enough to worry about compensating for it.

#### Age Groups

|         |       |
| ------- | ----- |
| Mean    | 18.59 |
| STD     | 2.4   |
| Minimum | 15    |
| 25%     | 17    |
| 50%     | 18    |
| 75%     | 21    |
| Maximum | 22    |
![[Pasted image 20251127145536.png|300]]

We can see a significant drop in samples for teens and older patients (81+).  Our samples are skewed significantly towards the 21-80 age group, so any future models would have to account for that.

#### Length of Stay

|         |       |
| ------- | ----- |
| Mean    | 10.78 |
| STD     | 5.64  |
| Minimum | 1     |
| 25%     | 6     |
| 50%     | 11    |
| 75%     | 15    |
| Maximm  | 20    |
![[Pasted image 20251128111351.png|300]]
This graph shows that a large portion of the sampled patients stayed for 10-15 days. The data doesn't deviate too much however, as there are at least 30 samples for each part of days admitted. 


#### Medication Amount

|         |      |
| ------- | ---- |
| Mean    | 8.04 |
| STD     | 4.24 |
| Minimum | 1    |
| 25%     | 4    |
| 50%     | 8    |
| 75%     | 12   |
| Maximum | 15   |
![[Pasted image 20251128111741.png|300]]
This graph tells us that most respondents had 9 active prescriptions.  We an also see that there there are small dips for responses at 6 and 10 total prescriptions.
$$
\frac{b}{a}
$$
#### Diagnosis

|         |      |
| ------- | ---- |
| Mean    | 2.83 |
| STD     | 1.44 |
| Minimum | 1    |
| 25%     | 2    |
| 50%     | 3    |
| 75%     | 4    |
| Maximum | 5    |
![[Pasted image 20251128112015.png|300]]
Here we can see that most patients had 1-2 active diagnoses during their stay at the hospital. However the data is spread pretty even, with nearly 80 people having 5 active diagnoses during their hospital stay.


### Readmission Comparisons
![[Pasted image 20251128125057.png|300]]![[Pasted image 20251128125819.png|300]]
![[Pasted image 20251128125852.png|300]]
Looking at these graphs, a highly readmitted patient would likely be 81+ years old, male/female (small margin), and prescribed 5 or 10 medications within the last 30 days.  
### At Risk Age groups
The riskiest group age group in the sample is the 81+ group, with the 21-40yr group behind a couple percentage points. This makes sense, as old people are the ones who are closest to dying out of anyone, and young adults tend to be the most reckless out of any age group.

### Conclusion
In conclusion, hospitals need to account for the populations at most risk. This means training staff and creating facilities that factor in the age of the patient (i.e rails for elderly patients). Hospitals could also collaborate with nearby retirement homes so that patients could be held there instead of the hospital (taking up bed space).