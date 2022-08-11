# (Characteristics of Loanstatus)
## by (Israel Joseph)


## Dataset

The main data set contains 113,937 loans with 81 variables but the data that we would be working with contains 50650 loans and 14 variables 
    I'm most interested in the 'LoanStatus' feature, seeing how the borrowers that have defaulted or not defaulted behaves.
The data set can be downloded using this hyperlink [data source](https://www.google.com/url?q=https://s3.amazonaws.com/udacity-hosted-downloads/ud651/prosperLoanData.csv&sa=D&ust=1581581520570000)

## Data wrangling

The following features are used in the analysis;
* ListingNumber: The number that uniquely identifies the listing to the public as displayed on the website.	
* Term: The length of the loan expressed in months.
* Occupation: The Occupation selected by the Borrower at the time they created the listing.
* DebtToIncomeRatio: The debt to income ratio of the borrower at the time the credit profile was pulled. This value is Null if the debt to income ratio is not available. This value is capped at 10.01 (any debt to income ratio larger than 1000% will be returned as 1001%).
* BorrowerRate: The Borrower's interest rate for this loan.
* Listing_category: The category of the listing that the borrower selected when posting their listing
* ProsperRating: The Prosper Rating assigned at the time the listing was created between AA - HR.  Applicable for loans originated after July 2009.
* ProsperScore: A custom risk score built using historical Prosper data. The score ranges from 1-10, with 10 being the best, or lowest risk score. Applicable for loans originated after July 2009.
* IsBorrowerHomeowner: A Borrower will be classified as a homowner if they have a mortgage on their credit profile or provide documentation confirming they are a homeowner.
* LoanOriginationDate: The date the loan was originated.
* EmploymentStatus:The employment status of the borrower at the time they posted the listing.
* LoanOriginalAmount: The origination amount of the loan.
* IncomeRange: The income range of the borrower at the time the listing was created.
* LoanStatus: The current status of the loan: Cancelled,  Chargedoff, Completed, Current, Defaulted, FinalPaymentInProgress, PastDue. The PastDue status will be accompanied by a delinquency bucket.
    Then missing records with missing value were removed, the LoanOriginationDate data type was converted into pandas datatime object. The loan status feature was grouped into two category during cleaning the default(0) and Non-default(1), also i change the listing category from number to it variable using python replace method thats after changing it to a dictionary for better representation of the data.

## Summary of Findings

### Univariate Exploration

* For the loan status less than 20000 borrowers are likely to default (0), More than 30000 borrowers will likely not default (1).

* For the prosper score, the distribution shows a multimodal distribution with the score 8 having the largets count that is above 4000.

* For the proper rating distribution shows that individuals with the highest rating AA are the least in the population and D has the highest population above 5000.

* For the IsBorrrowerHomeOwner it shows an almost even distribution between borrowers who have a home and do not.

* The 'Term' distribution shows 36 months (5 years) were more populated in the data with about count above 40000.

* The 'LoanOriginationDate' feature shows that  the year 2007 and 2003 had the highest count above 10000 and 2014 with the least.

* The 'BorrowerRate' feature It has a first peak around 0.1 and then increased around 0.15 before decreasing then spiked toward 0.3. the largest peak was around 0.31 with a count of 3500.

* The DebtToIncomeRatio has most of it data around 0.1 to 1 and the largest peak around 0.2.

* The 'LoanOriginalAmount' column is widely distributed from 1000 to 30000 with 30000 having the lowest peak.

* The 'EmploymentStatus' feature shows that full-time employers were larger in number that is above 20000 with the least Not-employed.

* For IncomeRange feature Large numbers of the borrowers are of the 'IncomeRange' 25,000 - 74,999 range.

* The 'ListingCategory' distributon shows that a very large amount about 60000 get the loans for debt consolidation.

### Bivariate Exploration

* For the plot that shows the relationship of loan status and home owners, borrowers who did not default had equal counts of homeowners above 16000 unlike the borrowers that have defaulted.

* For the plot that shows the relationship of loan status and Term, borrowers who collected loans for three years had more counts above 10000 for both the defaulters and Non-defaulters.

* For the plot that shows the relationship of loan status and Employment status, both the default and Non-default borrowers had full-time and employed employment status as their highest count above 4000 and 10000 respectively.  

* For the plot that shows the relationship of loan status and Income range, both the default and Non-default borrowers had 25,000 - 49,999 and 50,000 - 74,999 IncomeRange as their highest count above 2000 and 80000 respectively.

* The BorrowerRate distribution by year shows that 2006 had about 0.2 with a slight fall to 2007 and a gradual increase till 2011 which was the highest rate about 0.25. A steady fall occurred from 2012 to 2014.

* For the heatmap plot that shows the Correlation Between BorrowerRate, LoanStatus, LoanOriginalAmount, ProsperScore and DebtToIncomeRatio. The Prosper Score shows a strong negative relationship with BorrowerRate.

* For the relationship between Borrowers rate and Proper rating, the plots shows that the higher the Prosper ratings, the lower the BorrowerRate while that of borrower rate and prosper score, poor Proper Score tends to have higher BorrowerRate it the decreases toward the best but their are fluctuation within the proper score from 1-10.

* For the distribution of Prosper score by loan status, The borrowers that do not default seems to be more distributed above the proper score of 8 unlike the defaulters that seem to be evenly distributed between 4 to 8 proper score while that of Borrower Rate by loan status shows that borrowers that do not default seems to be more distributed above the BorrowerRate of 0.2 unlike the defaulters that seem to be more distributed below 0.2 BorrowerRate.

* For the relationship Between Borrower homeowner and IncomeRange, majority of borrowers with out homes had an income range of $25,000 - 49,999

### Multivariate Exploration

* For the relationship between BorrowerRate, IncomeRange and Term, incomeRange had borrowers that defaulted with Borrower Rate above 0.2 while the non-defaulters were below 0.2.

* For the debtToIncomeRatio(AVG.) Relationship Between Income Range and Loan status, non employed borrowers with high income debt to income ratio would default

* For the relationship between BorrowerRate, ProsperScore and LoanStatus, prosper score increases the borrower rate increase also for both default(0) and Non-default(1) borrowers.


## Key Insights for Presentation

From the analysis, the loan data had more borrowers that are Non-defaulters(1) than those that defaulted(0) and the data set reveals that the higher the prosper ratings the lower the borrowerRate, the borrower rate for both the default(0) and Non-default(1) decreases progressively as the prosper score increases but most importantly non employed borrowers with high debt to income ratio would default
Changes were made to the plots in order for it to be ready for exploratory data analysis and those changes are as follows;
* The axis label and title were changed 
* Colour pallete was introduced for the line plot and categorical plot
* Also the color bar for the heatmap plot was changed to blue