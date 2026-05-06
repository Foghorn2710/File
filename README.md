CREATE DATABASE jagan;

USE jagan;

CREATE TABLE Employee (
    E_id INT,
    E_name VARCHAR(10),
    Age INT,
    Salary INT
);

INSERT INTO Employee VALUES (10, 'abhi', 25, 10000);
INSERT INTO Employee VALUES (20, 'rohith', 30, 9000);
INSERT INTO Employee VALUES (30, 'david', 28, 9000);

DELIMITER //

CREATE PROCEDURE emp_cursor()
BEGIN
    DECLARE done INT DEFAULT 0;
    DECLARE v_id INT;
    DECLARE v_sal INT;

    DECLARE c1 CURSOR FOR
        SELECT E_id, Salary FROM Employee;

    DECLARE CONTINUE HANDLER FOR NOT FOUND
        SET done = 1;

    OPEN c1;

    read_loop: LOOP

        FETCH c1 INTO v_id, v_sal;

        IF done THEN
            LEAVE read_loop;
        END IF;

        SELECT v_id AS Emp_ID,
               v_sal AS Emp_Salary;

    END LOOP;

    CLOSE c1;

END //

DELIMITER ;

CALL emp_cursor();
