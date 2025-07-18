# Palmora-Group-HR-Analysis
### Overview
#### The Palmoria Group, a manufacturing company based in Nigeria, is embroiled in issues bordering on gender inequality in its 3 regions. Unfortunately, the media recently published the news with the headline “Palmoria, the Manufacturing Patriarchy”. This doesn’t look good for the owners of the business, based on their ambition to scale the business to other regions and even overseas. Cases like this can only spiral downwards, revealing other issues like the gender pay gap, amongst other possible issues. The CEO of Palmoria, Mr Ayodeji Chukwuma, is keen to address these issues before they get out of hand. The CHRO, Mr Yunus Shofoluwe, has been assigned the task to identify key areas within the business that could give rise to issues and address them immediately. Mr Shofoluwe decided to recruit you as an HR Analytics expert to analyse the company’s HR data and come up with recommendations for management’s attention. “Now, the future of gender equality in Palmoria lies in your hands” – the exact words of Mr Shofoluwe before he handed the data to you.

### About the Data
##### Having uploaded the files successfully. Here's a quick summary of their contents:
### Employee Data (Palmoria Group emp-data_083200)
#### Contains employee-level information:
Name, Gender (some missing),Department (some marked as NaN), Salary (some missing for ex-employees), Location (regions: e.g., Lagos, Abuja, Kaduna)
and Rating (performance ratings)

<img width="598" height="990" alt="image" src="https://github.com/user-attachments/assets/1fac5d23-f575-4328-b97d-a2b42cb0a0f3" />


### Bonus Rules (Palmoria Group Bonus Rules_083311)
This contains:Department, Performance Rating (Very Poor, Poor, Average, Good, Very Good) and Bonus Percentage

<img width="1918" height="1004" alt="image" src="https://github.com/user-attachments/assets/ccbce3b7-f385-43a9-b23c-7fbca4501dcb" />

### Transforming the data
#### To begin the analysis and provide the insights requested, I perform the below transformations:
#### Clean the data by 
1. Replace missing gender with 'Undisclosed'
2. Remove employees with Null/blanks salaries (ex-employees)
3. Remove entries with Null/blanks departments
4. Removed Duplicates values
5. Unpivot the bonus rules into a usable format for computations.
6. Clean Column Names by
   a. Rename: Attribute to Rating
   b. Value → Bonus_Percentage
7. Created new tables for distinct columns of Gender,Department, Location, and Rating and adding index to them
#### Index tables
- Gender
<img width="883" height="395" alt="image" src="https://github.com/user-attachments/assets/72d7f966-793a-4a37-bd91-36d44f7b263c" />

- Department
  
<img width="854" height="543" alt="image" src="https://github.com/user-attachments/assets/572c8966-2af7-4edc-89d7-786e862949f8" />

- Location
  
<img width="912" height="447" alt="image" src="https://github.com/user-attachments/assets/352c7072-0ac2-4859-8fa0-c114b8462be8" />

- Rating
  
<img width="885" height="472" alt="image" src="https://github.com/user-attachments/assets/d7247d7e-3e05-4e14-9d16-7a6e6b15ede7" />

8. Merged all my index tables to Employee Data using merging with Left Joins getting all their ID and the Bonus_Percentage. This adds a new column Bonus_Percentage to each employee based on their department and rating.

<img width="1911" height="992" alt="image" src="https://github.com/user-attachments/assets/819b76e2-6f13-42a2-aad7-8cf3cf2353f3" />
9. Loaded the cleaned data into Power BI for analysis and visuals
10. Calculated Columns (in Power BI)
    
#### Using my Data View and create the following DAX columns:

- `Bonus_Amount = 'Palmoria Group emp-data_083200'[Salary] * 'Palmoria Group emp-data_083200'[Palmoria Group Bonus Rules_083311.Bonus_Percentage]`






CASE SCENARIO 
●  Analyse the company data and generate insights that the Palmoria management 
team would need to address 
● Your analysis should be visualised using appropriate charts 
● Your focus should be on gender-related issues within the organization and its 
regions 
● The insights required are based on your discretion. However, Mr Gamma, as an 
insider, has offered to give you pointers on areas you need to pay attention to  
Required: 
● Generally, there are two genders in the organization. However, some employees 
refused to disclose their gender. You would need to assign a generic gender status 
to these employees 
● Some employees are without a salary because they are no longer with the company. 
You will need to take those employees out 
● Lastly, some departments are indicated as “NULL”. These departments would also 
need to be taken out. 
Pointers from Mr Gamma 
1. What is the gender distribution in the organization? Distil to regions and 
departments 
2. Show insights on ratings based on gender 
3. Analyse the company’s salary structure. Identify if there is a gender pay gap. If 
there is, identify the department and regions that should be the focus of 
management 
4. A recent regulation was adopted which requires manufacturing companies to pay 
employees a minimum of $90,000 
● Does Palmoria meet this requirement? 
● Show the pay distribution of employees grouped by a band of $10,000. For example: 
● How many employees fall into a band of $10,000 – $20,000, $20,000 – $30,000, 
etc.? 
● Also visualize this by regions 
Case Questions 
5. Mr Gamma thought to himself that since you were already working on the employee 
data, you could help out with allocating the annual bonus pay to employees based on the 
performance rating. He handed you another data set that contains rules for making bonus 
payments and asked you to: 
●  Calculate the amount to be paid as a bonus to individual employees 
●  Calculate the total amount to be paid to individual employees (salary inclusive of 
bonus) 
● Total amount to be paid out per region and company-wide
