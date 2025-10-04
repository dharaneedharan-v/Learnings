
### 🔹 What is `%ROWTYPE` in PL/SQL?

- `%ROWTYPE` is used to declare a **record variable** that can hold an **entire row of a table or cursor**.
- Instead of declaring one variable for each column, `%ROWTYPE` lets you grab all columns at once.
- Not able to print the entire row datatype if it will through an error. hold all the column in a single variable alone... 


---

### 🔹 Syntax

```
variable_name table_name%ROWTYPE;

```

---

### 🔹 Example

Suppose you have a `Student` table with columns:

`Student_id`, `First_name`, `Last_name`, `Age`.

Instead of doing this:

```
DECLARE
    v_id Student.Student_id%TYPE;
    v_fname Student.First_name%TYPE;
    v_lname Student.Last_name%TYPE;
    v_age Student.Age%TYPE;

```

You can simply do this:

```
DECLARE
    v_student Student%ROWTYPE;  -- can hold a full row
BEGIN
    SELECT *
    INTO v_student
    FROM Student
    WHERE Student_id = 102;

    DBMS_OUTPUT.PUT_LINE('ID: ' || v_student.Student_id);
    DBMS_OUTPUT.PUT_LINE('Name: ' || v_student.First_name || ' ' || v_student.Last_name);
    DBMS_OUTPUT.PUT_LINE('Age: ' || v_student.Age);
END;
/

```

---

### 🔹 Benefits of `%ROWTYPE`

1. **Saves time** → no need to declare each column individually.
2. **Avoids errors** → if the table structure changes (e.g., data type of a column changes), your code stays valid.
3. **Cleaner code** → especially useful for `SELECT * INTO`.

---

👉 In short: **`%ROWTYPE` creates a variable that represents an entire row of a table (or cursor) with all its columns.**


![[Pasted image 20250929211845.png]]



