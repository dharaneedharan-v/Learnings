




```plsql
set serveroutput on;
declare
type rec_demo is record(v_1 employees.first_name%type,
                        v_2 employees.salary%type,
                        v_3 departments.department_name%type);
v_demo       rec_demo;

begin
  select e.first_name, e.salary, d.department_name into v_demo
  from employees e, departments d
  where e.department_id = d.department_id
  and employee_id = 102;

  dbms_output.put_line(v_demo.v_1 || ' ' || v_demo.v_2 || ' ' || v_demo.v_3);
end;
/
```
### 1️⃣ Concept in simple words

- **What it is:** A **record** is a composite variable in PL/SQL that can store multiple related values together. Each value is called a **field**.
- **Why we need it:** Instead of creating separate variables for each related piece of data, a record lets you group them under **one variable**, making code cleaner and easier to manage.

---

### 2️⃣ Connect to what you know

- In **SQL**, a row has multiple columns.
- A **record** is like a **box** where each field corresponds to a column (or a piece of related data).
- You can access fields using the dot `.` operator: `record_name.field_name`.

---

### 3️⃣ Syntax / Declaration

### a) User-defined record

```
DECLARE
   TYPE emp_rec_type IS RECORD (
      emp_id   NUMBER,
      emp_name VARCHAR2(50),
      salary   NUMBER
   );
   emp_rec emp_rec_type; --  main variable  and record data type  variable (user defined )
BEGIN
   emp_rec.emp_id := 101;
   emp_rec.emp_name := 'John';
   emp_rec.salary := 5000;
END;

```

**Key points:**

- `TYPE ... IS RECORD` defines the structure of the record.
- `emp_rec` is the actual variable of that record type.
- Each field can have a different datatype.

---

### 4️⃣ How it works in practice

```
DECLARE
   TYPE student_rec_type IS RECORD (
      student_id   NUMBER,
      student_name VARCHAR2(100),
      grade        CHAR(1)
   );
   
   
   stud  student_rec_type;  -- 
BEGIN
   -- Assign values to fields
   stud.student_id := 1;
   stud.student_name := 'Alice';
   stud.grade := 'A';

   -- Access fields
   DBMS_OUTPUT.PUT_LINE('Student: ' || stud.student_name || ', Grade: ' || stud.grade);
END;

```


First stud as var  , assign  the datatype is student_rec_type inside the declare the datatype.. as you needed.  

**Step-by-step explanation:**

1. `stud` is a single record variable with three fields.
2. Values are assigned to each field individually.
3. Each field can be accessed using `stud.field_name`.

---

### 5️⃣ Takeaway

- A **record** is a **single PL/SQL variable** that groups multiple related values.
- It is flexible and allows you to store structured data easily.
- Each field can be of a different datatype, and you access them using the dot operator.