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

9. Loaded the cleaned data into Power BI for analysis and visuals.

10. Calculated Columns (in Power BI)
    
#### Using my Data View and create the following DAX columns:

- `Bonus_Amount = 'Palmoria Group emp-data_083200'[Salary] * 'Palmoria Group emp-data_083200'[Palmoria Group Bonus Rules_083311.Bonus_Percentage]`
  
- `New_Salary = 'Palmoria Group emp-data_083200'[Salary] + 'Palmoria Group emp-data_083200'[Bonus_Amount]`
  


- `Average_Female_Salary = CALCULATE(AVERAGE('Palmoria Group emp-data_083200'[Salary]),'Palmoria Group emp-data_083200'[Gender]="Female")`
  
- `Average_Male_Salary = CALCULATE(AVERAGE('Palmoria Group emp-data_083200'[Salary]),'Palmoria Group emp-data_083200'[Gender]="Male")`
  
- `Compliance_Percentage = DIVIDE([Compliant_Employees],COUNTROWS('Palmoria Group emp-data_083200'))`
  
- `Compliant_Employees = CALCULATE(COUNTROWS('Palmoria Group emp-data_083200'),'Palmoria Group emp-data_083200'[Salary] >=90000)`
  
- `Compliant_Employees = CALCULATE(COUNTROWS('Palmoria Group emp-data_083200'),'Palmoria Group emp-data_083200'[Salary] >=90000)`
  
- `Total_Compensation_Paid = SUM('Palmoria Group emp-data_083200'[New_Salary])`

## Visualization Dashboard Walkthrough 

<img width="1301" height="793" alt="image" src="https://github.com/user-attachments/assets/e9d57523-ad0c-4b2b-8000-448f003c9dbf" />

1. Gender Distribution
   - Objective: Gender representation across the company, by region and department.
     
<img width="394" height="305" alt="image" src="https://github.com/user-attachments/assets/172c4170-f395-422b-8586-080107e67c39" /><br>

<img width="314" height="357" alt="image" src="https://github.com/user-attachments/assets/14a134c5-ea64-4746-8d23-8b1757bbd62f" /><br>
 
<img width="412" height="314" alt="image" src="https://github.com/user-attachments/assets/c623a291-06a8-4e50-9e8c-af3da08e52a7" />
  
   - Insight:  It was clear that Male Employees are more than the female in the company at large with male being 49.45% and Female being 46.14%. It is also clear that male staff are many in all the location than female staff. Product Management, Legal, sales, Support, Accounting and Marketing Department has more male employees than others which mean 6 Departments out of the 12 Department has more Male staff but only training Department has the equal number of Male Staff and female Staff

2. Performance Ratings by Gender
   - Objective: To identify if performance ratings show any gender bias.

<img width="538" height="333" alt="image" src="https://github.com/user-attachments/assets/ca77cd5b-b7a7-423d-8e6f-b5669a221526" />

 - Insight:  It was clear that 1020 Male Employees has the highest rating of Average while 155 Male Employees has the least rating of Very Poor though more women are rate Good and very Good thank men.
     
3. Salary Analysis & Gender Pay Gap
  - Objective: To reveal whether there's a gender pay disparity.
    
       A. Average Salary by Gender
<img width="374" height="253" alt="image" src="https://github.com/user-attachments/assets/8ab3538f-cbb9-430f-b632-f3713167d8d9" />

      B. Salary by Gender and Department
<img width="517" height="311" alt="image" src="https://github.com/user-attachments/assets/c1803f20-aa57-4e6f-a7c9-f6d1725c2c69" />

    C. Salary by Gender and Location
<img width="531" height="127" alt="image" src="https://github.com/user-attachments/assets/0eda24ed-db04-4412-a8b6-b1e96122704d" />

- Insight:  It was clear that 1020 Male Employees has the highest rating of Average while 155 Male Employees has the least rating of Very Poor though more women are rate Good and very Good thank men.

4. Pay Band Distribution
 - Objective: To understand income distribution and check compliance with the $90,000 minimum regulation.
   
A. Create Pay Band Column

 - Use a calculated column in DAX:
   
   - `Pay_Band = 
SWITCH(
    TRUE(),
    [Salary] < 10000, 1,
    [Salary] < 20000, 2,
    [Salary] < 30000, 3,
    [Salary] < 40000, 4,
    [Salary] < 50000, 5,
    [Salary] < 60000, 6,
    [Salary] < 70000, 7,
    [Salary] < 80000, 8,
    [Salary] < 90000, 9,
    [Salary] < 100000, 10,
    11
)`

B. Pay Band Chart

<img width="723" height="517" alt="image" src="https://github.com/user-attachments/assets/4f9a7c9f-5c49-4285-a020-1c43338304a1" />



C. Pay Band by Region

<img width="748" height="504" alt="image" src="https://github.com/user-attachments/assets/23d64426-dc5f-42f6-9989-1d1698513346" />

- Insight to Watch For: Many Employees were paid below $90000 in all the location which means that Palmoria did not meet this requirement 

● Show the pay distribution of employees grouped by a band of $10,000. For example: 
● How many employees fall into a band of $10,000 – $20,000, $20,000 – $30,000, etc.? 

<img width="646" height="456" alt="image" src="https://github.com/user-attachments/assets/f2610deb-b1a9-475e-b4e4-b1df0eb92948" />

● Also visualize this by regions 

<img width="754" height="500" alt="image" src="https://github.com/user-attachments/assets/226183c9-242e-4730-815f-a1401e8d4ce6" />

Case Questions 
6. Mr Gamma thought to himself that since you were already working on the employee 
data, you could help out with allocating the annual bonus pay to employees based on the 
performance rating. He handed you another data set that contains rules for making bonus 
payments and asked you to: 
●  Calculate the amount to be paid as a bonus to individual employees 

<img width="496" height="390" alt="image" src="https://github.com/user-attachments/assets/9771fb14-9fa0-4be9-856e-4a26de32ad9a" />

●  Calculate the total amount to be paid to individual employees (salary inclusive of bonus) 

<img width="733" height="495" alt="image" src="https://github.com/user-attachments/assets/319587c1-88cc-41d3-a7b1-604fc7054795" />


● Total amount to be paid out per region and company-wide
<img width="724" height="501" alt="image" src="https://github.com/user-attachments/assets/a5f66c21-f31e-4d1d-bb97-54a1b78ac34c" />

<img width="416" height="157" alt="image" src="https://github.com/user-attachments/assets/51dba078-5c18-46e2-b1b1-72646649971e" />


