
A collection is an ordered group of elements having the same data type.
Each element is identified by a unique subscript that represents its position in the collection.



![[Pasted image 20251003230413.png]]


PL/SQL provides three collection types −

- Index-by tables or Associative array
- Nested table
- Variable-size array or V-array

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

