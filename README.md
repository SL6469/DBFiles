# DBFiles
Files Project for Database Management Spring 2016
Payroll Database

Enclosed in the accompanying zip file are three files:

 employees.txt – A listing of a company’s employees, and some demographics for them.

 sales.txt – A listing of the sales orders and the base used for commissions.

 hours.txt – A listing of weekly hours for each employee

The files are each text files using tab delimiters, and the first row of each file includes the field name.

Business Rules

 Any hourly employee who works more than 40 hours in a week earns 1.5 times their hourly 

rate for the portion over 40 hours.  If someone earns $10/hour and works 40 hours, they should 

get paid ($10/hour * 40 hours) + (1.5 * $10/hour * 5) =  $475.00

 Sales employees earn a base salary plus commission.  The commission rate is stored in the 

employee record.  For example, if a sales person sells $20,000 in a week and earns 3% 

commission, they earn $600 in commission plus their hourly base.

 The president and the sales manager (identified by their titles in the employee file) earn 

commission on all sales. 

Program #1 – Create, Delete, Modify Employees

Create a program that uses the command line to create a new employee, delete an existing one, or 

modify an existing one.

The first command line argument will be one of ADD, DEL, or MOD (case doesn’t matter)

The command line for ADD will prompt for each of the fields used to initialize an employee:

tbriggs$ ./employee add 

Enter new Employee ID

12383

Enter new Last Name

Smith

Enter new First Name

John

Enter new Department

Time Travel

Enter new Title

The Doctor

Enter new Salary

100032.33

Enter new Per

Annum

Enter new Commission

0.0

Enter new Tax ID

1234566

CSC371 - Database 1 Spring 2015 

CSC371 – Files Lab 

Enter new Street Address

42 Tardis Way

Enter new City

Cockeysville

Enter new State

Maryland

Enter new Zip

21401

Enter new Country

United States

Enter new Phone

410-323-3333

Writing employee

The command line for MOD will be followed with n the employee id number to change, then one of the 

following field names:  ID, LASTNAME, FIRSTNAME, DEPARTMENT, TITLE, SALARY, PER, 

COMMISSION, TAXID, STREET, CITY, STATE, ZIP, COUNTRY, PHONE; then the new value.

tbriggs$ ./employee mod 12383

What field to change: 

lastname

What new value: 

Jones

The command line for DEL will be followed with n the employee id number to delete

tbriggs$ ./employee del 12383

Removing 12383 Smith John

The desired changes will be applied to the text file by creating a data file with the changes and then 

renaming them new file to over-write the old file. 

Note: if you are using UNIX tools (Linux, OSX, or MobaXterm) you can use command-line tools such 

as less, cut, grep, and vi to inspect the contents of the file.

Hint: it might be a good idea to not over-write your original file during debugging – write it to a 

temporary location, inspect it, and verify everything is good.  When you have your program working, 

then you can remove the original file and rename or move the new file into place.  

Program #2 – Commission Computation

This program accepts a starting and end ending date on the command line.  It will read each sales 

order from the “sales.txt” file, find the matching salesman from the “employees.txt” file and compute 

the total commission for the salesman for the given period.  The data will be written to a text-file called 

“commissions.txt” that will be formatted as one entry per line, with the employee id, the total sales, and 

the total commission, with a tab delimiter and “currency” format as in the following example.  

Remember that “President” and “Sales Manager” get a commission on total sales.  If someone has 0 

sales, then they should have a record in the file.

CSC371 - Database 2 Spring 2015 

CSC371 – Files Lab 

tbriggs$ ./sales 01/01/2015 01/07/2015

Read 30 employees

tbriggs$ cat commissions.txt 

1233 3209.18 96.28

499 1513.97 45.42

1225 735.84 22.08

1142 19446.70 19.45

1281 1630.41 24.46

162 6726.57 100.90

647 19446.70 0.00

470 724.98 43.50

431 4092.29 245.54

1909 813.46 48.81

Program #3 – Report It

The last program involves reading the hours worked and computing the total pay for the given pay 

period and reporting the salaries, showing for each department what the total hours worked.  You will 

need to sort the output (remember our discussion about sort/report keys)

The hours.txt file is from a different computer system – only hourly employees are listed, and it 

reports hours in blocks – so that if there is not an employee id, it will be same as the last previous 

employee id.

Note: As a simplifying assumption, it is OK to assume that the start and end dates will comprise a one 

week period, and that the dates will always be valid.  Remember from the business rules how pay is 

computed from salaried employees.

CSC371 - Database 3 Spring 2015 

CSC371 – Files Lab 

CSC371 - Database 4 Spring 2015 

CSC371 – Files Lab 

Deliverables

For this project, you will submit a zip file or tar.gz file of your project source – and only your project 

source.  The file must be named “lab1-your-last-name.zip” or “lab1-your-last-name.tgz” or it will 

not be graded and you will receive a final grade of zero for not following simple instructions!

Upload the file to the Google classroom dropbox for the assignment.

Your project should include a “makefile” that will compile your code, and then allow me to run your 

project.  Basically here is what I’m going to do:

$ mkdir smith

$ cd smith

$ cp $SOURCE/lab1-smith.zip

$ unzip lab1-smith.zip

$ make

$ cp $SOURCE/text/* .

$ ./employee add  < input.txt

$ ./employee mod 323433

$ ./employee del 324433

$ ./sales 01/01/2015 01/08/2015

$ ./hours 01/02/2015 01/09/2015

If you are using Java, then you’ll need to make some shell scripts to do the same thing:

#!/bin/bash

java Employee $*

And include them in your project directory – google this if you need to

I’m going to compare your output to the examples I’ve included in the lab – and if there are significant 

differences, you’ll get points deducted.  

Hint: remove debugging output, and make yours look like mine – seriously, you’ll loose points

I am not going to poke through your code, I’m goig to following the previous script – on sloop – so you 

should be able to do something similar.  The source text files will be like the ones I’ve given you (but 

with different data).
