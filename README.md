# Data Transformation Examples

## Introduction

Data transformation is a crucial step in data processing that involves converting data from its raw form into a more useful format. This process can be accomplished using various tools and languages, such as SQL and Python. The following examples illustrate common data transformation tasks in SQL and Python, showcasing how to manipulate and analyze data effectively.

## SQL Data Transformations

1. **Select Specific Columns**
   ```sql
   SELECT name, age FROM employees;
   ```
   **Description:** Extracts only the `name` and `age` columns from the `employees` table.

2. **Filter Data**
   ```sql
   SELECT * FROM sales WHERE amount > 1000;
   ```
   **Description:** Retrieves rows from the `sales` table where the `amount` is greater than 1000.

3. **Sort Data**
   ```sql
   SELECT * FROM products ORDER BY price DESC;
   ```
   **Description:** Orders the rows in the `products` table by `price` in descending order.

4. **Aggregate Data**
   ```sql
   SELECT department, COUNT(*) AS employee_count FROM employees GROUP BY department;
   ```
   **Description:** Counts the number of employees in each department and groups the results by department.

5. **Join Tables**
   ```sql
   SELECT orders.id, customers.name FROM orders JOIN customers ON orders.customer_id = customers.id;
   ```
   **Description:** Combines data from the `orders` and `customers` tables based on matching `customer_id` and `id`.

6. **Calculate Average**
   ```sql
   SELECT AVG(salary) AS average_salary FROM employees;
   ```
   **Description:** Computes the average `salary` of employees in the `employees` table.

7. **Update Data**
   ```sql
   UPDATE employees SET salary = salary * 1.05 WHERE department = 'Sales';
   ```
   **Description:** Increases the `salary` of employees in the `Sales` department by 5%.

8. **Delete Data**
   ```sql
   DELETE FROM logs WHERE created_at < '2024-01-01';
   ```
   **Description:** Removes rows from the `logs` table where the `created_at` date is before January 1, 2024.

9. **Insert Data**
   ```sql
   INSERT INTO products (name, price) VALUES ('New Product', 29.99);
   ```
   **Description:** Adds a new row to the `products` table with the name 'New Product' and a price of 29.99.

10. **Concatenate Columns**
    ```sql
    SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM customers;
    ```
    **Description:** Combines `first_name` and `last_name` columns to create a `full_name` column in the `customers` table.

11. **String Replacement**
    ```sql
    UPDATE users SET email = REPLACE(email, '@old-domain.com', '@new-domain.com');
    ```
    **Description:** Replaces the domain part of the `email` column from '@old-domain.com' to '@new-domain.com' in the `users` table.

12. **Date Functions**
    ```sql
    SELECT EXTRACT(YEAR FROM CURRENT_DATE) AS current_year;
    ```
    **Description:** Extracts the current year from the current date.

13. **Use Subquery**
    ```sql
    SELECT * FROM orders WHERE customer_id IN (SELECT id FROM customers WHERE country = 'USA');
    ```
    **Description:** Retrieves orders for customers whose `country` is 'USA' using a subquery.

14. **Find Duplicate Records**
    ```sql
    SELECT name, COUNT(*) FROM users GROUP BY name HAVING COUNT(*) > 1;
    ```
    **Description:** Identifies duplicate `name` entries in the `users` table.

15. **Create Index**
    ```sql
    CREATE INDEX idx_employee_name ON employees(name);
    ```
    **Description:** Creates an index on the `name` column in the `employees` table to improve query performance.

16. **Convert to Upper Case**
    ```sql
    SELECT UPPER(name) AS upper_name FROM employees;
    ```
    **Description:** Converts the `name` column to uppercase.

17. **Date Arithmetic**
    ```sql
    SELECT DATE_ADD(CURRENT_DATE, INTERVAL 30 DAY) AS future_date;
    ```
    **Description:** Adds 30 days to the current date.

18. **Extract Substring**
    ```sql
    SELECT SUBSTRING(name, 1, 5) AS short_name FROM customers;
    ```
    **Description:** Extracts the first 5 characters from the `name` column.

19. **Group By and Aggregate**
    ```sql
    SELECT department, SUM(salary) AS total_salaries FROM employees GROUP BY department;
    ```
    **Description:** Computes the total `salary` for each department.

20. **Calculate Percentage**
    ```sql
    SELECT name, (salary / (SELECT SUM(salary) FROM employees)) * 100 AS salary_percentage FROM employees;
    ```
    **Description:** Calculates the percentage of each employee's salary relative to the total salary of all employees.

## Python Data Transformations

1. **Select Specific Columns**
   ```python
   import pandas as pd
   df = pd.read_csv('employees.csv')
   df_selected = df[['name', 'age']]
   ```
   **Description:** Selects only the `name` and `age` columns from the DataFrame.

2. **Filter Data**
   ```python
   df_filtered = df[df['amount'] > 1000]
   ```
   **Description:** Filters rows where the `amount` column value is greater than 1000.

3. **Sort Data**
   ```python
   df_sorted = df.sort_values(by='price', ascending=False)
   ```
   **Description:** Sorts the DataFrame by `price` in descending order.

4. **Aggregate Data**
   ```python
   df_grouped = df.groupby('department').size().reset_index(name='employee_count')
   ```
   **Description:** Groups the DataFrame by `department` and counts the number of rows in each group.

5. **Join DataFrames**
   ```python
   df_joined = pd.merge(orders, customers, left_on='customer_id', right_on='id')
   ```
   **Description:** Merges two DataFrames based on matching `customer_id` and `id`.

6. **Calculate Average**
   ```python
   average_salary = df['salary'].mean()
   ```
   **Description:** Computes the average value of the `salary` column.

7. **Update Data**
   ```python
   df.loc[df['department'] == 'Sales', 'salary'] *= 1.05
   ```
   **Description:** Increases the `salary` of employees in the 'Sales' department by 5%.

8. **Delete Data**
   ```python
   df_cleaned = df[df['created_at'] >= '2024-01-01']
   ```
   **Description:** Filters rows where the `created_at` date is on or after January 1, 2024.

9. **Insert Data**
   ```python
   new_row = {'name': 'New Product', 'price': 29.99}
   df = df.append(new_row, ignore_index=True)
   ```
   **Description:** Appends a new row to the DataFrame with specified values.

10. **Concatenate Columns**
    ```python
    df['full_name'] = df['first_name'] + ' ' + df['last_name']
    ```
    **Description:** Creates a new column `full_name` by concatenating `first_name` and `last_name`.

11. **String Replacement**
    ```python
    df['email'] = df['email'].str.replace('@old-domain.com', '@new-domain.com')
    ```
    **Description:** Replaces occurrences of '@old-domain.com' with '@new-domain.com' in the `email` column.

12. **Date Functions**
    ```python
    from datetime import datetime
    current_year = datetime.now().year
    ```
    **Description:** Retrieves the current year using Python's `datetime` module.

13. **Extract Substring**
    ```python
    df['short_name'] = df['name'].str[:5]
    ```
    **Description:** Extracts the first 5 characters from the `name` column to create a `short_name` column.

14. **Group By and Aggregate**
    ```python
    df_grouped = df.groupby('department')['salary'].sum().reset_index(name='total_salaries')
    ```
    **Description:** Groups the DataFrame by `department` and calculates the sum of `salary` for each group.

15. **Calculate Percentage**
    ```python
    total_salaries = df['salary'].sum()
    df['salary_percentage'] = (df['salary'] / total_salaries) * 100
    ```
    **Description:** Computes the percentage of each employee's `salary` relative to the total salary.

16. **Convert to Upper Case**
    ```python
    df['name'] = df['name'].str.upper()
    ```
    **Description:** Converts all values in the `name` column to uppercase.

17. **Date Arithmetic**
    ```python
    df['future_date'] = pd.to_datetime(df['created_at']) + pd.DateOffset(days=30)
    ```
    **Description:** Adds 30 days to the `created_at` date for each row.

18. **Find Duplicate Records**
    ```python
    duplicates = df[df.duplicated(['name'], keep=False)]
    ```
    **Description:**

 Identifies rows with duplicate values in the `name` column.

19. **Add a New Column with Default Value**
    ```python
    df['bonus'] = 0.0
    ```
    **Description:** Adds a new column `bonus` with a default value of 0.0.

20. **Change Data Type**
    ```python
    df['price'] = df['price'].astype(float)
    ```
    **Description:** Converts the `price` column to the `float` data type.

## Conclusion

These examples illustrate how SQL and Python can be used to transform and manipulate data effectively. SQL provides powerful querying capabilities for working directly with databases, while Python, with its `pandas` library, offers versatile data manipulation features for various data processing needs. Understanding these transformations is essential for data analysts and engineers to clean, prepare, and analyze data efficiently.
