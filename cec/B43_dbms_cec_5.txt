DECLARE
    CURSOR EMPCURSOR IS
    SELECT
        *
    FROM
        EMPLOYEE;
    ID      INT;
    NAME    VARCHAR(100);
    SALARY  INT;
    CONTACT VARCHAR(10);
BEGIN
    OPEN EMPCURSOR;
    LOOP
        FETCH EMPCURSOR INTO ID, NAME, SALARY, CONTACT;
        EXIT WHEN EMPCURSOR%NOTFOUND;
        DBMS_OUTPUT.PUT_LINE('*****************************************');
        DBMS_OUTPUT.PUT_LINE('NAME: '
                             ||NAME);
        DBMS_OUTPUT.PUT_LINE('ID: '
                             ||ID);
        DBMS_OUTPUT.PUT_LINE('SALARY: '
                             ||SALARY);
        DBMS_OUTPUT.PUT_LINE('CONTACT: '
                             ||CONTACT);
        DBMS_OUTPUT.PUT_LINE('*****************************************');
    END LOOP;
END;
/