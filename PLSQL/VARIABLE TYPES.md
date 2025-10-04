
1) Global  Variable 
2) local  Variable


local :

A example for the syntax .

```plsql
declare 
dharani varchar(200) := 'PLSQL';
begin 
dbms_output.put_line(dharani);
end ;
/
```



global : 

```plsql
declare 
dharani varchar(200) := 'PLSQL';
    begin 
    declare
    dharan varchar(100) := 'dharan';
    v_dd integer := 20000;
    begin 
    dbms_output.put_line('Name of the employee is : '||dharan);
    dbms_output.put_line('This is a salaray report for the ' || dharan || ':'|| v_dd);
    dbms_output.put_line('this is a global var  : '|| dharani);
    end ;

dbms_output.put_line(dharani);
end ;
/
```

output : 
```python 
Name of the employee is : dharan
This is a salaray report for the dharan:20000
this is a global var  : PLSQL
PLSQL
```

if we use the same var it will be overidden as  the last value 

```plsql

declare 
dharani varchar(200) := 'PLSQL';
    begin 
    declare
    dharan varchar(100) := 'dharan';
    v_dd integer := 20000;
    dharani varchar(100) := 'Laravel';
    begin 
    dbms_output.put_line('Name of the employee is : '||dharan);
    dbms_output.put_line('This is a salaray report for the ' || dharan || ':'|| v_dd);
    dbms_output.put_line('this is a global var  : '|| dharani);
    
    end ;

dbms_output.put_line(dharani);
end ;
/
```

output:
```python 
Name of the employee is : dharan
This is a salaray report for the dharan:20000
this is a global var  : Laravel
PLSQL
```
