


Here’s a super simple version:

- **User Input:** Data entered by the user.
    
    **Example:** `name = input("Enter name: ")`
    
- **Substitution Variable:** Placeholder replaced by a value at runtime.
    
    **Example:** `SELECT * FROM employees WHERE dept = &dept;`


Example : 



**Substitution Variable:** A placeholder in code or a query that is replaced by a value at runtime.

**Example (SQL):**

```sql
SELECT * FROM employees WHERE department = &dept;

```

Here, `&dept` is a substitution variable that gets replaced with a department name when the query runs.




Example : 


```plsql

declare

v_salary integer ;

begin 

select e_salary into v_salary from Employee where salary = &user_input_var ; -- user input for the salary to enter to get form the databases .

dbms_output.put_line(v_salary);

end ;
/

```

