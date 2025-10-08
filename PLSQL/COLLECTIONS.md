
A collection is an ordered group of elements having the same data type.
Each element is identified by a unique subscript that represents its position in the collection.



<img width="1919" height="867" alt="Screenshot 2025-10-03 230411" src="https://github.com/user-attachments/assets/6bee1ca6-8616-448f-bdbe-cb89a0676f3b" />


PL/SQL provides three collection types −

- Index-by tables or Associative array
- Nested table
- Variable-size array or V-array



> HINT : Storing the Val by one by one Means it is a List .
> Storing the Val by in a single Initialization is called Array. 
-----


### Index By Tables :


<img width="1022" height="436" alt="Screenshot 2025-10-03 231414" src="https://github.com/user-attachments/assets/576915b9-2d6f-4f4a-b5e5-a62d63a90788" />



Example : 

Static data

```plsql 
-- set serveroutput on;  

declare
    type T_var 
    is table of varchar(20) 
    index by PLS_INTEGER;
    
    
    v_emp T_var;
begin
    v_emp(1) := 'dharani';
    v_emp(2) := 'PLSQL';
    v_emp(5) := 'developer';

    dbms_output.put_line(v_emp(1));
    dbms_output.put_line(v_emp(5));
end;
/

```

dynamic data : 

```plsql 
-- set serveroutput on;  


declare
    type T_var 
    -- is table of varchar(20) 
    is table of Student%rowtype
    index by PLS_INTEGER;
    
    
    v_emp T_var;
begin
    

select * 
into v_emp
from Student 
where id = 102;
-- select * from Student where id = 102 ;
    dbms_output.put_line(v_emp(10).salary); -- According to the column name to get the output. 
end;
/


```

We can change the datatype according to that requirements...





----


# NESTED TABLE

<img width="1051" height="424" alt="Screenshot 2025-10-03 234435" src="https://github.com/user-attachments/assets/de0178ed-b9ca-4e62-a738-88b7b67b6553" />


In the Associaltive we will give the index of key word  , By default it is a Integer Indexed one....



Example :


For the List : 

```plsql 
declare 

type T_var 
is table of varchar2(20); -- no need to mention the index of in the nexted table


v_emp T_var:= T_var();  -- we must initinalzise the constructor here 

begin 
v_emp.extend(2);  -- We must specify the lenght how many records 
v_emp(1):= 'dharani';
v_emp(2):= 'SQL';
dbms_output.put_line(v_emp(1));
dbms_output.put_line(v_emp(2));
end ;
/


```

For the array : 

```plsql 
declare 

type T_var 
is table of varchar2(20); -- no need to mention the index of in the nexted table


v_emp T_var:= T_var('dharani ' , 'SQL');  -- we must initinalzise the constructor here 

begin 
--v_emp.extend(2);  -- No need to specify the extend as we are using the array 
--v_emp(1):= 'dharani';
--v_emp(2):= 'SQL';
dbms_output.put_line(v_emp(1));
dbms_output.put_line(v_emp(2));
end ;
/
```

Dynamic Fetching :

```plsql

declare

type T_var
is table of employee%rowtype;

v_emp T_var := T_var();

begin
v_emp extend(2);
select * 
into v_emp  
from employee 
where id = 106 ;
dbms_output.put_line(v_emp(2).first_name); -- should mention which column other wise error it will throw 

end;
/

```

To handle the Errors Like Not Null values :

```plsql 

declare 

type T_var 
is table of varchar2(20) not null ; -- no need to mention the index of in the nexted table


v_emp T_var:= T_var('dharani ' , '');  -- we must initinalzise the constructor here 

begin 
--v_emp.extend(2);  -- No need to specify the extend as we are using the array 

dbms_output.put_line(v_emp(1));
dbms_output.put_line(v_emp(2));
end ;
/
```

output :

```python 
declare
*
ERROR at line 1:
ORA-06502: PL/SQL: value or conversion error
ORA-06512: at line 9
```

----

# VARRAY 

<img width="1041" height="420" alt="Screenshot 2025-10-04 095051" src="https://github.com/user-attachments/assets/f45327ae-40fb-4014-acbb-02eae01782f6" />


Example :


```plsql 

declare 
type T_var is VARRAY(10) of varchar2(20); -- set the upper bound and Key word VARRAY in caps 
v_emp T_var:= T_var()  ; -- Call the constructor 
begin
v_emp.extend(4);  -- exdend it as we storing it in the List.
v_emp(1):= 'dharani';
v_emp(2):= 'sql';
dbms_output.put_line(v_emp(2));
end ;
/
```
