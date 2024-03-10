CREATE TABLE EMPLOYEE (
    ID INT PRIMARY KEY,
    NAME VARCHAR(100) NOT NULL,
    SALARY INT NOT NULL,
    CONTACT VARCHAR(10)
);

CREATE OR REPLACE PROCEDURE INSERT_DUMMY_EMP IS
BEGIN
    INSERT INTO EMPLOYEE (ID, NAME, SALARY, CONTACT)
    VALUES
        (1, 'John', 10000, '1234567890'),
        (2, 'Doe', 8000, '1234567890'),
        (3, 'Jane', 30000, '1234567890'),
        (4, 'Doe', 40000, '1234567890'),
        (5, 'Doe', 14000, '1234567890');
END INSERT_DUMMY_EMP;
/

DECLARE
    CURSOR EMPCURSOR IS
    SELECT
        SALARY,
        NAME
    FROM
        EMPLOYEE;
    SALARY INT;
    NAME   VARCHAR(100);
BEGIN
    INSERT_DUMMY_EMP;
    OPEN EMPCURSOR;
    LOOP
        FETCH EMPCURSOR INTO SALARY,NAME;
        EXIT WHEN EMPCURSOR%NOTFOUND;
        IF SALARY < 15000 THEN
            DBMS_OUTPUT.PUT_LINE('Updating '
                                 ||NAME
                                 || ' salary from '
                                 || SALARY
                                 || ' to '
                                 || (SALARY + 5000));
            UPDATE EMPLOYEE
            SET
                SALARY = SALARY + 5000
            WHERE
                SALARY < 15000
                AND NAME = NAME;
        END IF;
    END LOOP;

    CLOSE EMPCURSOR;
END;
/