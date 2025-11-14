**Project Title: *Titanic Passenger Survival Data Analysis***



* **Objective:**



To analyze the Titanic passenger dataset to derive insights like survival rate, passenger demographics, and class-based survival, using MySQL for data storage and management.



* **Dataset Overview:**



The Titanic dataset contains information about 891 passengers, detailing attributes such as Name, Sex, Age, Ticket number, Fare paid, Cabin, Embarked port, and survival status.



* **Dataset Source:**



Dataset Description: Contains attributes like PassengerId, Survived, Pclass, Name, Sex, Age, SibSp, Parch, Ticket, Fare, Cabin, Embarked, etc.



* **ER Diagram \& Database Design**



**Entity: Passenger**

![alt text](<Screenshot 2025-11-14 141904-1.png>)


* **ER Diagram (Text-based)**



+------------------------------+

|         Passenger            |

+------------------------------+

| PassengerID (PK)             |

| Survived                     |

| Pclass                       |

| Name                         |

| Sex                          |

| Age                          |

| SibSp                        |

| Parch                        |

| Ticket                       |

| Fare                         |

| Cabin                        |

| Embarked                     |

+------------------------------+



* **Database Schema Creation**



CREATE DATABASE TitanicDB;



USE TitanicDB;



CREATE TABLE passengers (

PassengerID INT AUTO\_INCREMENT PRIMARY KEY,

Survived TINYINT NOT NULL,

Pclass TINYINT NOT NULL,

Name VARCHAR(255) NOT NULL,

Sex VARCHAR(10) NOT NULL,

Age FLOAT,

SibSp TINYINT NOT NULL,

Parch TINYINT NOT NULL,

Ticket VARCHAR(50) NOT NULL,

Fare FLOAT NOT NULL,

Cabin VARCHAR(50),

Embarked VARCHAR(10)

);



* **Data Import**



1. Save the Titanic dataset in CSV format.

2. Use MySQL's LOAD DATA INFILE command.



LOAD DATA INFILE '/path/to/titanic.csv'

INTO TABLE passengers

FIELDS TERMINATED BY ','

ENCLOSED BY '"'

LINES TERMINATED BY '\\n'

IGNORE 1 ROWS;

(Ensure the file path is correct and file permissions allow reading)



* **Sample Queries**



1. View all data:



SELECT * FROM passengers;



2. Count of survivors vs non-survivors:



SELECT Survived, COUNT(*) AS count

FROM passengers

GROUP BY Survived;



3. Average age of passengers:



SELECT AVG(Age) AS AvgAge FROM passengers;



4. Survival rate by gender:



SELECT Sex, AVG(Survived) AS SurvivalRate

FROM passengers

GROUP BY Sex;



5. Survival rate by passenger class:



SELECT Pclass, AVG(Survived) AS SurvivalRate

FROM passengers

GROUP BY Pclass;



* Future Extensions:



1. Add predictive modeling for survival prediction.
2. Visualize data patterns (e.g., age vs survival, fare distributions).
3. Build an interface for data entry and live analysis.



