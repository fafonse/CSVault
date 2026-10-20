- Using the [Gun Violence Dataset](https://github.com/harsh1399/DS2500-Data_Wrangling/tree/main/Module_Assignment-2/gun-violence-data)
- Using the modern [Gun Violence Dataset 2](https://github.com/dxzys/Gun-Violence-Data/tree/main)
- 2013-2018


Previous research using similar datasets has often been descriptive, and not really doing any deeper analysis on correlations between variables. Pew Research Center and the John Hopkins Center have both published recent reports about 2024 gun violence, but mostly just describe the data instead of exploring potential relationships. This includes infographics and ranking different states, but not much about correlation between variables. 
This motivates my analysis as I want to extend these descriptive analyses by examining the relationship between the variables and focusing on the comparison of Utah to the rest of the nation. Specifically I want to see how Utah compares in the *times the incidents occur* (seasons, months, etc.), the amount of participants involved, and correlations with location data within the state as a whole (is the south of Utah more or less violent, and is that consistent with other states?

- 3 fields to research:
	- Incident characteristics
		- Participant count, vicitims, deaths, gun type
	- Geographic characteristics
		- Where within the state is the higher frequency?
			- Account for population diffferences
			- and age :/
	- Temporal
		- Season, month, days
		- What years did Utah do worse comparitively to other states?

For the dataset's I'll use, it will be the *Gun Violence Dataset* originally provided in Module 2 as well as a modern dataset that does not provide the same amount of detail. These datasets both use the Gun Violence Archive as their primary source, mainly just scraping the data into a comprehensive CSV file. The first dataset provides information concerning gun violence from 2013-2018, with additional data concerning the gun type and detailed information of the participants involved. The second dataset has modern results up to 2026, but does not include the same amount of information regarding participants or weapon type. I believe that while the data from the first dataset is more useful in finding information, the second dataset will be far more relevant as it isn't a decade old. 
Both datasets will be downloaded from their official Github repositories. The 2013-2018 dataset has additional documentation regarding it's specific format for the additional details included, and the newer dataset is rather self-explanatory and includes minor documentation. 
I plan on using visualization such as histograms and scatterplots to not only provide some basic descriptive infographs in my final conclusion, but to also check the data for any inconsistencies and differences between my two datasets. For answering the questions regarding the temporal frequency of gun violence, I will use a histogram to see if I can spot any trends visually. I will then use a Spearman correlation test to check if the month/day of week is related to gun violence. 
For limitations, I foresee that any data that uses the 2013-2018 dataset is going to be quite outdated. I will also be limited to the rather simplistic modern dataset if I want to have more relevant results. For that reason, I'll be doing a large part of my analysis using the newer dataset, and I will use the older dataset only to answer the questions regarding the gun type and participant details. 