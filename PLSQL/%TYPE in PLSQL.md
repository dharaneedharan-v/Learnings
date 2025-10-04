
##### You don't know the variable type Means You can use the %type to the particular variable. 

If you declare a variable without a datatype it will through an error  to avoid that only we are 
using the %type of the column in the database 




Example  : 


```plsql

declare 
v_name Student.First_name%type; -- Same Table 
v_name Collage.Student.First_name%type ; -- different db -> shema -> column value..\
v_Fullname  v_name%type ; -- Assiging the same variable datatype to another new variable(FullName)

begin

select First_name into v_name from Student where Student_id = 102 ;

dbms_output.put_line(v_name);



end ;
/

```

![[Pasted image 20250929200700.png]]