/*
1.Write a stored procedure by the name of PROC1 that accepts two varchar strings as parameters. Your procedure 
should then determine if the first varchar string exists inside the varchar string. For example, if string1 = ‘DAC’ 
and string2 = ‘CDAC, then string1 exists inside string2.  The stored procedure should insert the appropriate message 
into a suitable TEMPP output table. Calling program for the stored procedure need not be written.
*/
show tables;
drop table tempp;
create table tempp
(
fir varchar(30),
sec varchar(30),
res varchar(30)
);
show tables;
delimiter //
create procedure PROC1(string1 varchar(30),string2 varchar(30))
begin
     if (instr(string1,string2)>0 or instr(string2,string1)>0) then
        insert into tempp values('string1','string2','Exist');
     else
        insert into tempp values('string1','string2','Not Exist');
	end if;
end;//
call PROC1('DAC','CDAC');
call PROC1('ADI','NGL');
drop procedure PROC1;
select * from tempp;



/*2.Create a stored function by the name of FUNC1 to take three parameters, the sides of a triangle. The function 
should return a Boolean value:- TRUE if the triangle is valid, FALSE otherwise. A triangle is valid if the length of 
each side is less than the sum of the lengths of the other two sides. Check if the dimensions entered can form a valid
 triangle. Calling program for the stored function need not be written.*/
 create table tempp1
 (
 fir int,
 sec varchar(30)
 );
 delimiter //
 create function FUNC1(a float,b float,c float)
returns boolean
as Triangle exceptions;
 begin
     if  ((a+b>c) and (a+c>b) and (b+c>a)) then 
         insert into tempp1 values(a,'Triangle');
	else 
        insert into tempp1 values(a,'Not Triangle');
 end;//
 drop function FUNC1;
 call FUNC1(3,4,5);
 select * from tempp1;
 