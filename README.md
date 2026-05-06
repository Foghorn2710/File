-- Create Table
CREATE TABLE Employee (
    E_id NUMBER,
    E_name VARCHAR2(10),
    Age NUMBER,
    Salary NUMBER
);

-- Insert Records
INSERT INTO Employee VALUES (10, 'abhi', 25, 10000);
INSERT INTO Employee VALUES (20, 'rohith', 30, 9000);
INSERT INTO Employee VALUES (30, 'david', 28, 9000);

-- Cursor Program
SET SERVEROUTPUT ON;

DECLARE
    CURSOR c1 IS
        SELECT E_id, Salary FROM Employee;

    v_id Employee.E_id%TYPE;
    v_sal Employee.Salary%TYPE;

BEGIN
    DBMS_OUTPUT.PUT_LINE('Emp ID    Emp Salary');
    DBMS_OUTPUT.PUT_LINE('----------------------');

    OPEN c1;

    LOOP
        FETCH c1 INTO v_id, v_sal;

        EXIT WHEN c1%NOTFOUND;

        DBMS_OUTPUT.PUT_LINE(v_id || '        ' || v_sal);
    END LOOP;

    CLOSE c1;
END;
/
