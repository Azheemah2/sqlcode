# sqlcode
introduction to Database assignment

import sqlite3 as db

connection = db.connect("BouncyCastleRental.db")
cursor = connection.cursor()



query = """
CREATE TABLE IF NOT EXISTS 'Customer' (
    'Customer_ID'           INTEGER,
    'FirstName'             TEXT,
    'LastName'              TEXT,
    'HouseNumber'           INTEGER,
    'PostCode'              TEXT,
    'PhoneNumber'           INTEGER,

    PRIMARY KEY('Customer_ID' AUTOINCREMENT)    
)"""


query1 = """
CREATE TABLE IF NOT EXISTS 'BouncyCastle' (
    'BouncyCastle_ID'       INTEGER,
    'Name'                  TEXT,
    'Dimensions'            TEXT,
    'colour'                TEXT,
    'MaximumOccupants'      INTEGER,
    'HirePrice'             REAL,
    PRIMARY KEY('BouncyCastle_ID' AUTOINCREMENT)    
)"""


query2 = """
CREATE TABLE IF NOT EXISTS 'BookingInfo' (
    'BookingInfo_ID'        INTEGER,
    'Customer_ID'           INTEGER,
    'BouncyCastle_ID'       INTEGER,
    'BookedDate'            TEXT,
    'ReturnDate'            TEXT,
    'PaymentType'           TEXT,
    PRIMARY KEY('BookingInfo_ID' AUTOINCREMENT),
    FOREIGN KEY (Customer_ID) REFERENCES Customer(Customer_ID) ON UPDATE RESTRICT ON DELETE RESTRICT,
    FOREIGN KEY (BouncyCastle_ID) REFERENCES BouncyCastle(BouncyCastle_ID) ON UPDATE RESTRICT ON DELETE RESTRICT    
)"""

cursor.execute(query)
cursor.execute(query1)
cursor.execute(query2)

connection.commit()
connection.close()
