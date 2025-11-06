# Java_JPA_Hibernate-lab-04

We compile the application with this command:

```
mvn -q -DskipTests compile
```

## TABLE_PER_CLASS checks

After running

```
mvn -q exec:java@TABLE_PER_CLASS
```

mysql -uroot -proot -D DB_LAB_04_TABLE_PER_CLASS -e "SHOW TABLES;"

mysql -uroot -proot -D DB_LAB_04_TABLE_PER_CLASS -e "SELECT * FROM Customer; SELECT * FROM Employee; SELECT * FROM Executive;"

**Expected**

Customer has id=1, name, discount=10.0

<img width="918" height="435" alt="image" src="https://github.com/user-attachments/assets/fb0d7b15-4296-46c7-8345-7a5e2d2e9653" />

Employee has id=2, name, salary=1000.0

<img width="927" height="429" alt="image" src="https://github.com/user-attachments/assets/4ca4ef45-1cf7-4582-af01-789ce39178d8" />

Executive has id=3, name, salary=2000.0, bonus=30.0

<img width="923" height="435" alt="image" src="https://github.com/user-attachments/assets/4947517a-93ac-42f4-a6e9-f2d4d0f2d2e8" />

## TABLE_PER_HIERARCHY checks

After running 

```
mvn -q exec:java@TABLE_PER_HIERARCHY
```

mysql -uroot -proot -D DB_LAB_04_TABLE_PER_HIERARCHY -e "SHOW TABLES; DESCRIBE Person; SELECT id,name,DTYPE,salary,discount,bonus FROM Person ORDER BY id;"

**Expected**

Single table Person with DTYPE values: CUSTOMER(1), EMPLOYEE(2), EXECUTIVE(3) and the respective columns populated.

<img width="1200" height="519" alt="image" src="https://github.com/user-attachments/assets/8ecf9204-7a61-4932-9616-1eba288af3f7" />

## TABLE_PER_SUBCLASS checks

After running:

```
mvn -q exec:java@TABLE_PER_SUBCLASS:
```

mysql -uroot -proot -D DB_LAB_04_TABLE_PER_SUBCLASS -e "SHOW TABLES;"

mysql -uroot -proot -D DB_LAB_04_TABLE_PER_SUBCLASS -e "SELECT * FROM Person ORDER BY id; SELECT * FROM Employee ORDER BY id; SELECT * FROM Executive ORDER BY id; SELECT * FROM Customer ORDER BY id;"

**Expected**

Person has 3 rows (ids 1,2,3; names).

<img width="924" height="570" alt="image" src="https://github.com/user-attachments/assets/9d5096e8-a34e-464f-9673-5d271eaf17d1" />

Employee has rows for id=2 and id=3 (exec inherits employee).

<img width="931" height="571" alt="image" src="https://github.com/user-attachments/assets/39c0fe0a-f2de-4ed2-961b-dfaf87f1f1b3" />

Executive has row id=3 (bonus).

<img width="1017" height="567" alt="image" src="https://github.com/user-attachments/assets/7b30bbd2-67fa-4008-9b7b-6df862b2deef" />

Customer has row id=1 (discount).

<img width="928" height="571" alt="image" src="https://github.com/user-attachments/assets/db92ccfb-dc30-47d3-b0c2-84f916428e2b" />
