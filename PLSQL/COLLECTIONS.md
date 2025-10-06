
A collection is an ordered group of elements having the same data type.
Each element is identified by a unique subscript that represents its position in the collection.



![[Pasted image 20251003230413.png]]


PL/SQL provides three collection types −

- Index-by tables or Associative array
- Nested table
- Variable-size array or V-array



> HINT : Storing the Val by one by one Means it is a List .
> Storing the Val by in a single Initialization is called Array. 
-----


### Index By Tables :


![[Pasted image 20251003231441.png]]



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

![[Pasted image 20251003234437.png]]


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

![[Pasted image 20251004095052.png]]


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