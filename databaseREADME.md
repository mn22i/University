create table Department(
Department_id number(6) not null,
Department_name varchar(30) not null,
constraint Department_id primary key(Department_id)
);
• Create Student table :
create table Student(
Student_id number(6) not null,
First_name varchar(20) not null,
Last_name varchar(25) not null,
Email varchar(25), 
Address varchar(30),
constraint Student_id primary key(Student_id),
constraint Student_email unique(Email),
Department_id number(6) constraint Student_FK references Department(Department_id)
);
• Create Course table :
create table Course( 
Course_id number(6) not null,
Course_name varchar(30) not null,
Credit_hours number(2) not null, 
constraint Course_id primary key (Course_id),
Department_id number(6) constraint Course_FK references Department(Department_id )
);
 Create Lecturer table :
create table Lecturer ( 
Lecturer_id number(6) not null, 
Lecturer_name varchar(20) not null,
Email varchar(30) not null, 
constraint Lecturer_id primary key (Lecturer_id),
constraint Lecturer_email unique(Email),
Department_id number(6) constraint Lecturer_FK references Department(Department_id)
);
• Create Section table :
create table Section ( 
Section_id number(6) not null,
Class# varchar(2),
constraint Section_id primary key (Section_id),
Course_id number(6) constraint Section_CFK references Course(Course_id),
Lecturer_id number(6) constraint Section_LFK references Lecturer(lecturer_id)
);
• Create stu_enrolls table :
create table stu_enrolls (
Enrollment_date date not null,
Section_id number(6) not null,
Student_id number(6) not null,
constraint stu_enrolls primary key (Student_id,section_id)
);
alter table stu_enrolls add constraint stu_nroll_FK foreign key(student_id) references 
Student(student_id) on delete cascade;
alter table stu_enrolls add constraint sec_nroll_FK foreign key(section_id) references 
Section(section_id) on delete cascade;
• Insert records into the department table :
INSERT INTO Department VALUES( 144001 ,'IT');
INSERT INTO Department VALUES( 144002 ,'IS');
INSERT INTO Department VALUES( 144003 ,'CS');
Insert records into the student table :
INSERT INTO Student VALUES( 112200, 'Sara','AL-harbi',' Saraa1234@gmail.com','jeddah', 
144001);
INSERT INTO Student VALUES( 112211, 'Rama','AL-mohammedi',' 
Rama1423@gmail.com','jeddah', 144002);
INSERT INTO Student VALUES( 112201, 'Shaimaa','AL-W',' Sh@gmail.com','riyadh', 
144003);
INSERT INTO Student VALUES( 112230, 'Reem','AL-ali',' reem908@gmail.com','abha 
',144003);
INSERT INTO Student VALUES( 112244, 'Amani','AL-harbi',' amani@gmail.com','makkah 
',144002);
INSERT INTO Student VALUES( 112254, 'Suha','AL-harbi',' suha@gmail.com','makkah 
',144001);
INSERT INTO Student VALUES( 112250, 'Lamar','AL-harbi',' 
lamar@gmail.com','rabigh',144003);
• Insert records into Course table :
INSERT INTO Course VALUES( 101 ,'computer network',5,144001);
INSERT INTO Course VALUES( 102 ,'programming I',4,144003);
INSERT INTO Course VALUES( 103 ,'programming II',4,144003);
INSERT INTO Course VALUES( 104 ,'programming III',4,144003);
INSERT INTO Course VALUES( 105 ,'database',6,144002);
INSERT INTO Course VALUES( 106 ,'operating system',6,144003);
INSERT INTO Course VALUES( 107 ,'human-computer intration',4,144001);
• Insert records into Lecturer table :
INSERT INTO Lecturer VALUES( 142122 ,'Ahlam',' Al-Mohammedi
','Ahlam146@kau.edu.sa',144001); 
INSERT INTO Lecturer VALUES( 547125 ,'Maryam',' 
Alzhrani','maryam001@kau.edu.sa',144002); 
INSERT INTO Lecturer VALUES( 142356 ,'Norah',' Al-ali','nor@kau.edu.sa',144003);
INSERT INTO Lecturer VALUES( 176423 ,'Shahad', ' AL-harbi','shahad@kau.edu.sa',144002);
INSERT INTO Lecturer VALUES( 142673 ,'Suad',' Alshehri','suad@kau.edu.sa',144001);
INSERT INTO Lecturer VALUES( 105028 ,'Amal', ' Alghamdi','amal@kau.edu.sa',144003);
INSERT INTO Lecturer VALUES( 102648,'Ahmad', ' Algarni','ahmad@kau.edu.sa',144003);
Insert records into Section table :
INSERT INTO Section VALUES( 122013 ,C2,101,142122);
INSERT INTO Section VALUES( 120054 ,A3,102,142356);
INSERT INTO Section VALUES( 129836,12,103,102648);
INSERT INTO Section VALUES( 129443,B9,104,102648);
INSERT INTO Section VALUES( 129464,A2,105,547125);
INSERT INTO Section VALUES( 143379,23,106,142356);
INSERT INTO Section VALUES( 143679,20,107,142122);
INSERT INTO Section VALUES( 234760,10,101,142673);
INSERT INTO Section VALUES( 334761,17,105,176423);
INSERT INTO Section VALUES( 538766,17,103,105028);
• Insert records into stu_enrolls table:
INSERT INTO stu_enrolls values('06/29/2022', 112200, 122013);
INSERT INTO stu_enrolls values('06/28/2022', 112200, 129836);
INSERT INTO stu_enrolls values('06/28/2022', 112200, 129464);
INSERT INTO stu_enrolls values('06/29/2022', 112211, 122013);
INSERT INTO stu_enrolls values('06/30/2022', 112211, 129836);
INSERT INTO stu_enrolls values('06/30/2022', 112211, 129464);
INSERT INTO stu_enrolls values('06/30/2022', 112201, 122013);
INSERT INTO stu_enrolls values('06/29/2022', 112201, 129836);
INSERT INTO stu_enrolls values('06/27/2022', 112201, 120054);
INSERT INTO stu_enrolls values('06/26/2022', 112230, 143379);
INSERT INTO stu_enrolls values('06/26/2022', 112230, 129443);
INSERT INTO stu_enrolls values('06/29/2022', 112244, 143379);
INSERT INTO stu_enrolls values('06/26/2022', 112244, 129443);
INSERT INTO stu_enrolls values('06/23/2022', 112254, 143379);
INSERT INTO stu_enrolls values('06/23/2022', 112250, 143379);
• Retrieve first name and last name as ‘Lecturer Name ‘ from lecturer and department tables
select first_name | | last_name AS "Lecturer Name"
from Lecturer
where first_name like '%r%';
Retrieve Course_Name and Section_id and class# on condition Crrdit_hour>5
Select course_name ,credit_hours ,class#
From course , section
Where course.course_id= section.course_id AND credit_hours > 5 ;
Retrieve Student_id,first_name,Department_Name
Select student_id, first_name, department_name
From department , student
Where department.department_id= student.department_id ;
Retrieve Student_id,Email
Select Student_id, email
From student;
Retrieve Section_id,class#,Course_id ,Lecturer_id
Select section_id, course_name, class#
From course, section
where course.course_id = section.course_id;
Update Credit_hour = 6 for Course_id =101
UPDATE course
SET Credit_hours= 6
WHERE Course_ID = 101;
Delete Section_id=53766
delete from section 
where section_id = 538766;
Alter table Student rename column address to city;





