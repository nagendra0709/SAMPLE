# SAMPLE
SAMPLE DATA CLEANING
import numpy as np 
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv('train.csv')
df.info()
a = df.describe()
df.isnull().sum()
df['Gender'].fillna(df['Gender'].mode()[0], inplace = True)
df['Married'].fillna(df['Married'].mode()[0],inplace = True)
df['Dependents'].fillna(df['Dependents'].mode()[0],inplace = True)
df['Self_Employed'].fillna(df['Self_Employed'].mode()[0],inplace = True)
#df['LoanAmount'].value_counts()
df['Credit_History'].fillna(df['Credit_History'].mode()[0],inplace = True)
lst = ['LoanAmount', 'Loan_Amount_Term']
for i in lst:
    df[i].fillna(df[i].mean(),inplace = True)
df['ApplicantIncome'].hist(bins = 100)
df['CoapplicantIncome'].hist(bins = 20)
df['Total_Income'] = df['ApplicantIncome']+df['CoapplicantIncome']
df['Total_Income_Log'].skew()
df['Total_Income'].hist(bins = 20)
df['Total_Income_Log'] = np.log(df['Total_Income'])
df['Total_Income'].hist(bins = 20)
plt.hist(df['ApplicantIncome'],df['Loan_Status'])
plt.xlabel('ApplacantIncome')
plt.ylabel('Loan_Status')
plt.title('Income vs Loan_Status')
plt.show()

#boxplot
df.boxplot(column='ApplicantIncome',by=['Education', 'Gender'])
df['ApplicantIncome_Log'].skew()
df['ApplicantIncome_Log'] = np.log(df['ApplicantIncome'])
