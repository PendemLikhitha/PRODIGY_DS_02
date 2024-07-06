# ProdigyInfoTech_TASK2
## TASK 2: Data Cleaning and Exploratory Data Analysis (EDA) on Titanic Dataset

This project demonstrates how to perform data cleaning and exploratory data analysis (EDA) on the Titanic dataset from Kaggle.

## Dataset

The dataset used in this project is the Titanic dataset, available on [Kaggle](https://www.kaggle.com/c/titanic/data).

## Visualizations

1. **Survival Rate by Gender**: Bar chart showing the survival rate of passengers by gender.
2. **Survival Rate by Passenger Class**: Bar chart showing the survival rate of passengers by passenger class.
3. **Age Distribution of Passengers**: Histogram showing the distribution of ages among passengers.

## How to Run

1. Clone the repository.
2. Ensure you have the necessary libraries installed (`pandas`, `matplotlib`, `seaborn`).
3. Place the dataset (`Titanic-Dataset.csv`) in the same directory as the script.
4. Run the script (`titanic_data_analysis.py`) to generate the visualizations.

## Code

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from IPython.display import display

# Load the Titanic dataset
titanic_data = pd.read_csv(r'C:\Users\91812\Pictures\Titanic-Dataset.csv')
# Display the first few rows of the dataset
display(titanic_data.head())

# Check the summary statistics of numerical columns
print(titanic_data.describe())

# Check for missing values
print(titanic_data.isnull().sum())
```
![Screenshot 2024-07-06 220339](https://github.com/PendemLikhitha/PRODIGY_DS_02/assets/159911587/19a3d56a-9076-4fcb-a207-ceb5e3f99319)
![Screenshot 2024-07-06 220346](https://github.com/PendemLikhitha/PRODIGY_DS_02/assets/159911587/9b99ac30-9e7e-4e7f-be58-3dc152245248)


```python
# Check for missing values and clean data as needed
# Fill missing ages with the median age
titanic_data['Age'] = titanic_data['Age'].fillna(titanic_data['Age'].median())

# Convert categorical variables to appropriate formats
titanic_data['Sex'] = titanic_data['Sex'].astype('category').cat.codes
titanic_data['Embarked'] = titanic_data['Embarked'].astype('category').cat.codes

# Check the total number of survivors by gender
survivors_by_gender = titanic_data.groupby('Sex')['Survived'].mean()

# Print the percentage of women who survived
print(f"% of women who survived: {survivors_by_gender[0]*100}")

# Print the percentage of men who survived
print(f"% of men who survived: {survivors_by_gender[1]*100}")
```
![Screenshot 2024-07-06 220541](https://github.com/PendemLikhitha/PRODIGY_DS_02/assets/159911587/bf4acada-d0ac-4457-bbd8-edc771785bcf)

```python
# Visualize survival rate by gender
sns.barplot(x='Sex', y='Survived', data=titanic_data, ci=None)
plt.xlabel('Gender (0 = Female, 1 = Male)')
plt.ylabel('Survival Rate')
plt.title('Survival Rate by Gender')
plt.show()
```

### Survival Rate by Gender
![Screenshot 2024-07-06 220902](https://github.com/PendemLikhitha/PRODIGY_DS_02/assets/159911587/64a39575-9f80-466e-93a0-768c27642753)



```python
# Visualize survival rate by passenger class
sns.barplot(x='Pclass', y='Survived', data=titanic_data, ci=None)
plt.xlabel('Passenger Class')
plt.ylabel('Survival Rate')
plt.title('Survival Rate by Passenger Class')
plt.show()
```
### Survival Rate by Passenger Class
![Screenshot 2024-07-06 220910](https://github.com/PendemLikhitha/PRODIGY_DS_02/assets/159911587/7b1f17b3-2a9c-47d1-847d-6e9e7d4188e0)


```python
# Visualize age distribution
plt.hist(titanic_data['Age'], bins=20, edgecolor='black')
plt.xlabel('Age')
plt.ylabel('Frequency')
plt.title('Age Distribution of Passengers')
plt.show()
```
### Age Distribution of Passengers
![Screenshot 2024-07-06 220916](https://github.com/PendemLikhitha/PRODIGY_DS_02/assets/159911587/b3d53577-05f7-44f9-a425-c1e81be5d214)


