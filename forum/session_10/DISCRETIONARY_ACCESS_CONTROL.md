# Binus University

This repository includes my personal homework for the course Introduction to Database Systems on forum session 10.

This forum has a requirement to give a grant and then revoke the user access named admin to have access for SELECT and
UPDATE query.

```mysql
# create and use the database
CREATE DATABASE latihan;
USE latihan;

# create the table
CREATE TABLE mahasiswa
(
    StudentID      INT         NOT NULL AUTO_INCREMENT,
    StudentName    VARCHAR(50) NOT NULL,
    StudentAddress TEXT        NOT NULL,
    PhoneNumber    VARCHAR(15) NOT NULL,
    Major          VARCHAR(50) NOT NULL,
    PRIMARY KEY (StudentID)
) ENGINE = InnoDB;

# create user name admin
CREATE USER 'admin'@'localhost' IDENTIFIED BY 'password';

# grant user
GRANT SELECT, UPDATE ON latihan.mahasiswa TO 'admin'@'localhost';

# revoke user
REVOKE SELECT, UPDATE ON latihan.mahasiswa TO 'admin'@'localhost';
```

Created by Rochman Ramadhani Chiefto Irawan ❤.
