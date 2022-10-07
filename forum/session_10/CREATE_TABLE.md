# Binus University

This repository includes my personal homework for the course Introduction to Database Systems on forum session 10.

```mysql
CREATE DATABASE binus_library;
USE binus_library;

# Tabel MSStudent
CREATE TABLE MsStudent
(
    StudentID      INT         NOT NULL AUTO_INCREMENT,
    StudentName    VARCHAR(50) NOT NULL,
    StudentAddress TEXT        NOT NULL,
    PhoneNumber    VARCHAR(15) NOT NULL,
    Major          VARCHAR(50) NOT NULL,
    PRIMARY KEY (StudentID)
) ENGINE = InnoDB;

# Tabel TrHeaderBorrowing
CREATE TABLE TrHeaderBorrowing
(
    BorrowID   INT NOT NULL AUTO_INCREMENT,
    StudentID  INT,
    BorrowDate DATE,
    INDEX (StudentID),
    FOREIGN KEY (StudentID) REFERENCES MSStudent (StudentID) ON DELETE RESTRICT ON UPDATE CASCADE,
    PRIMARY KEY (BorrowID)
) ENGINE = InnoDB;

# Tabel MsBook
CREATE TABLE MsBook
(
    BookID    INT          NOT NULL AUTO_INCREMENT,
    BookName  VARCHAR(100) NOT NULL,
    Author    VARCHAR(50)  NOT NULL,
    Publisher VARCHAR(100) NOT NULL,
    PRIMARY KEY (BookID)
) ENGINE = InnoDB;

# Tabel TrDetailBorrowing
CREATE TABLE TrDetailBorrowing
(
    BorrowID INT NOT NULL,
    BookID   INT NOT NULL,
    QTY      INT,
    INDEX (BorrowID),
    INDEX (BookID),
    FOREIGN KEY (BorrowID) REFERENCES TrHeaderBorrowing (BorrowID) ON DELETE RESTRICT ON UPDATE CASCADE,
    FOREIGN KEY (BookID) REFERENCES MsBook (BookID) ON DELETE RESTRICT ON UPDATE CASCADE,
    PRIMARY KEY (BorrowID, BookID)
) ENGINE = InnoDB;
```

Created by Rochman Ramadhani Chiefto Irawan ❤.
