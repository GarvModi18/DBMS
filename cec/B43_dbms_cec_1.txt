-- Write a program that will accept user’s choice as 1 or 2.
-- - If user enters 1 than accept principle amount ,rate,time
-- from user and calculate the simple interest si=(p*t*r)/100
-- -If user enters 2 than accept pi, r from user and calculate
-- the area of circle
DECLARE
    CHOICE    INT := &CH;
    PRINCIPLE DECIMAL(10, 2);
    RATE      DECIMAL(5, 2);
    YEARS     INTEGER;
    SI        DECIMAL(10, 2);
    PI        DECIMAL(10, 8);
    RADIUS    DECIMAL(5, 2);
    AREA      DECIMAL(10, 2);
BEGIN
    IF CHOICE = 1 THEN
        PRINCIPLE := &PRINCIPLE;
        RATE := &RATE;
        YEARS := &YEARS;
        SI := (PRINCIPLE*YEARS*RATE)/100;
        DBMS_OUTPUT.PUT_LINE('Simple Interest is '
                             || SI);
    ELSIF CHOICE = 2 THEN
        PI := &PI;
        RADIUS := &RADIUS;
        AREA := PI * RADIUS * RADIUS;
        DBMS_OUTPUT.PUT_LINE('Area of circle is '
                             || AREA);
    END IF;
END;
/