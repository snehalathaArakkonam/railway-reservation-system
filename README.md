# 🚆 Railway Reservation System

- 🎥 Youtube video for Step by Step Guide on Local Setup: https://www.youtube.com/watch?v=Wd2GlEJJJlw

---

## About

This project is about the **Railway Reservation System** which is used to view Train Schedule, search trains, Seat availability, Train timings. We can also enquire about fare of different trains. We can get information about train between two stations. We can book seats online. This provides a safe and secure seat reservation system.

---

## Online Train Information and Reservation

**This Website is built for following purpose:-**

- View Trains Schedule
- Search Trains
- Seat Availability
- Train Timings
- Fare Enquiry
- Trains Between Stations
- Booking seats online.
- Login and Logout Security
- Password Changes
- Payment Gateway
- Ticket Booking History

---

**The Admin have the following access to this website:-**

- Login
- Add Trains
- Update Trains
- Remove or cancel Trains
- View Trains
- Profile Edit
- Logout

---

**The Users have the following Access:-**

- Register
- Login
- View Trains
- Check Seat Availability
- Search Trains
- Train Availability and Fare Between Stations
- Book Tickets
- View Booking History
- View Profile
- Update Profile
- Change Password
- Logout

---

## Technologies Used

**1. Front-End Development:**
- HTML
- CSS
- Bootstrap

**2. Back-End Development:**
- Java [J2EE]
- JDBC
- Servlet
- Oracle (SQL)

---

## Software And Tools Required

| Tool | Download |
|------|----------|
| Git | https://www.youtube.com/watch?v=gv7VPQ4LZ7g |
| Java JDK 8+ | https://www.youtube.com/watch?v=O9PWH9SeTTE |
| Eclipse EE | https://www.youtube.com/watch?v=8aDsEV7txXE |
| Apache Maven | https://www.youtube.com/watch?v=jd2zx3dLjuw |
| Tomcat v8.0+ | https://youtu.be/mLFPodZO8Iw?t=903 |
| Oracle (SQL) / SQL PLUS | https://www.youtube.com/watch?v=ZYOqykEDSqU |
| Oracle SQL Developer | https://www.youtube.com/watch?v=2a1JKIGVtd0 |

---

## Dummy Database Initialization

**STEP 1:** Open SQL Plus OR SQL Developer

**STEP 2:** Login and connect to database using administrator username and password

**STEP 3:** Execute the below command first to create a new user:

```sql
ALTER SESSION SET "_ORACLE_SCRIPT"=TRUE;  
CREATE USER RESERVATION IDENTIFIED BY MANAGER;
GRANT DBA TO RESERVATION;
COMMIT;
```

> **NOTE:** If the above command fails for alter session issues, try to remove the first line and then execute it.

**STEP 4:** Now execute the below SQL query in the same terminal:

```sql
CONNECT RESERVATION/MANAGER;

CREATE TABLE "RESERVATION"."CUSTOMER"
(
  "MAILID" VARCHAR2(40) PRIMARY KEY,
  "PWORD"  VARCHAR2(20) NOT NULL,
  "FNAME"  VARCHAR2(20) NOT NULL,
  "LNAME"  VARCHAR2(20),
  "ADDR"   VARCHAR2(100),
  "PHNO"   NUMBER(12)   NOT NULL
);

CREATE TABLE "RESERVATION"."ADMIN"
(
  "MAILID" VARCHAR2(40) PRIMARY KEY,
  "PWORD"  VARCHAR2(20) NOT NULL,
  "FNAME"  VARCHAR2(20) NOT NULL,
  "LNAME"  VARCHAR2(20),
  "ADDR"   VARCHAR2(100),
  "PHNO"   NUMBER(12)   NOT NULL
);

CREATE TABLE "RESERVATION"."TRAIN"
(
  "TR_NO"    NUMBER(10)    PRIMARY KEY,
  "TR_NAME"  VARCHAR2(70)  NOT NULL,
  "FROM_STN" VARCHAR2(20)  NOT NULL,
  "TO_STN"   VARCHAR2(20)  NOT NULL,
  "SEATS"    NUMBER(4)     NOT NULL,
  "FARE"     NUMBER(6,2)   NOT NULL
);

CREATE TABLE "RESERVATION"."HISTORY"
(
  "TRANSID"  VARCHAR2(36) PRIMARY KEY,
  "MAILID"   VARCHAR2(40) REFERENCES "RESERVATION"."CUSTOMER"(MAILID),
  "TR_NO"    NUMBER(10),
  "DATE"     DATE,
  "FROM_STN" VARCHAR2(20) NOT NULL,
  "TO_STN"   VARCHAR2(20) NOT NULL,
  "SEATS"    NUMBER(3)    NOT NULL,
  "AMOUNT"   NUMBER(8,2)  NOT NULL
);

COMMIT;

INSERT INTO RESERVATION.ADMIN VALUES('admin@demo.com','admin','System','Admin','Demo Address 123 colony','9874561230');
INSERT INTO RESERVATION.CUSTOMER VALUES('snehalatha@demo.com','snehalatha','Snehalatha','','Arakkonam',9000000000);

INSERT INTO RESERVATION.TRAIN VALUES(10001,'JODHPUR EXP','HOWRAH','JODHPUR', 152, 490.50);
INSERT INTO RESERVATION.TRAIN VALUES(10002,'YAMUNA EXP','GAYA','DELHI', 52, 550.50);
INSERT INTO RESERVATION.TRAIN VALUES(10003,'NILANCHAL EXP','GAYA','HOWRAH', 92, 451);
INSERT INTO RESERVATION.TRAIN VALUES(10004,'JAN SATABDI EXP','RANCHI','PATNA', 182, 550);
INSERT INTO RESERVATION.TRAIN VALUES(10005,'GANGE EXP','MUMBAI','KERALA', 12, 945);
INSERT INTO RESERVATION.TRAIN VALUES(10006,'GARIB RATH EXP','PATNA','DELHI', 1, 1450.75);

INSERT INTO RESERVATION.HISTORY VALUES('BBC374-NSDF-4673','snehalatha@demo.com',10001,TO_DATE('02-FEB-2024'), 'HOWRAH', 'JODHPUR', 2, 981);
INSERT INTO RESERVATION.HISTORY VALUES('BBC375-NSDF-4675','snehalatha@demo.com',10004,TO_DATE('12-JAN-2024'), 'RANCHI', 'PATNA', 1, 550);
INSERT INTO RESERVATION.HISTORY VALUES('BBC373-NSDF-4674','snehalatha@demo.com',10006,TO_DATE('22-JULY-2024'), 'PATNA', 'DELHI', 3, 4352.25);

COMMIT;
```

**STEP 5:** Execute the below queries one by one to verify the tables were created successfully:

```sql
SELECT * FROM ADMIN;
SELECT * FROM CUSTOMER;
SELECT * FROM TRAIN;
SELECT * FROM HISTORY;
```

> **Note:** If any of the above commands fail, please fix them before proceeding to the next step.

---

## Importing and Running the Project Through Eclipse EE

**Step 0:** Open Eclipse Enterprise Edition. [Install if not available](https://www.youtube.com/watch?v=8aDsEV7txXE)

**Step 1:** Click On `File` > `Import` > `Git` > `Projects From Git` > `Clone Uri` > Paste the Repository URL:
```
https://github.com/snehalathaArakkonam/railway-reservation-system.git
```
> Next > Select Main Branch > Next > Finish

**Step 2.A:** Right Click on Project > `Run as` > `Maven Build` > In the goals field enter `clean install` > Apply > Run

**Step 2.B:** Right Click On Project > `Build Path` > `Configure Build Path` > `Libraries` > Remove And Update Any Libraries With Red Mark > Finish

**Step 3:** *(Only if Tomcat v8.0 is not configured in Eclipse)*
Right Click On Project > `Run As` > `Run On Server` > Select Tomcat v8.0 > (Select Tomcat V8.0 Installation Location If Asked) > Next > Add > Finish

**Step 4:** In The Server Tab > Double Click On Tomcat Server > `Ports` > Change The Port Number For `Http/1.1` To `8083` > Close And Save

**Step 5:** Right Click On Project > `Run As` > `Run On Server` > Select Tomcat V8.0 > Next > Add All > Done

**Step 6:** Open the site at → http://localhost:8083/trainbook/

**Step 7:** Default credentials for **Admin**:
- Username: `admin@demo.com`
- Password: `admin`

**Step 8:** Default credentials for **User**:
- Username: `snehalatha@demo.com`
- Password: `snehalatha`

---

## Screenshots

### 1. Login Page
![Login to Book Trains](https://user-images.githubusercontent.com/34605595/232219369-85b55a1d-6640-4821-941a-dcca08036fbe.png)

### 2. Register New User
![Register New User](https://user-images.githubusercontent.com/34605595/232219485-2b00949a-be20-44f7-b6c1-107213221f94.png)

### 3. User Profile
![View User Profile](https://user-images.githubusercontent.com/34605595/232219729-2720e50f-e14b-4253-831a-85c59e3054b3.png)

### 4. Search Trains Between Stations
![Search Trains Between Stations](https://user-images.githubusercontent.com/34605595/232220357-54b634d6-afae-427c-b3af-57b372b70906.png)

### 5. View Trains
![View Available Trains](https://user-images.githubusercontent.com/34605595/232219905-983eeefe-977b-40ad-a695-4ec577272dcc.png)

### 6. Book Trains
![Book Trains Project](https://user-images.githubusercontent.com/34605595/232220107-415b251f-90b9-4e07-aff8-e94d370927f6.png)

### 7. Payment Gateway
![Pay to Book Trains](https://user-images.githubusercontent.com/34605595/232220744-351c2c6d-e1f6-49ad-a11b-7680aa63dbe3.png)

### 8. Booked Ticket Information
![Show Booked Ticket Details](https://user-images.githubusercontent.com/34605595/232220935-654bda38-cbde-4203-84b8-3078a32ac6ec.png)

### 9. Ticket Booking History
![All Ticket Booking History](https://user-images.githubusercontent.com/34605595/232220491-3e7996cb-a54c-4375-a35a-6ab1d211a001.png)

### 10. Fare Enquiry
![Fare Enquiry between stations](https://github.com/snehalathaArakkonam/railway-reservation-system/raw/main/Screenshots/fareenquiry.png)

### 11. Change Password
![Change user Password](https://github.com/snehalathaArakkonam/railway-reservation-system/raw/main/Screenshots/passwordchange.png)

### 12. Add Trains By Admin
![Admin Home](https://github.com/snehalathaArakkonam/railway-reservation-system/raw/main/Screenshots/addtrains.png)

---

> #### "Suggestions and project improvements are invited"

**Snehalatha**  
*Project Leader*  
[![GitHub](https://img.shields.io/badge/GitHub-snehalathaArakkonam-181717?style=flat-square&logo=github)](https://github.com/snehalathaArakkonam/railway-reservation-system/tree/main)
