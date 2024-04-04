-- Create the Employees table
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(100),
    DepartmentID INT,
    Position VARCHAR(100),
    Salary DECIMAL(10, 2),
    HireDate DATE,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);

-- Create the Departments table
CREATE TABLE Departments (
    DepartmentID INT PRIMARY KEY,
    Name VARCHAR(100),
    ManagerID INT,
    Location VARCHAR(100),
    FOREIGN KEY (ManagerID) REFERENCES Employees(EmployeeID)
);

-- Add a department
INSERT INTO Departments (DepartmentID, Name, ManagerID, Location)
VALUES (1, 'Engineering', 101, 'Building A');

-- Add an employee
INSERT INTO Employees (EmployeeID, Name, DepartmentID, Position, Salary, HireDate)
VALUES (101, 'John Doe', 1, 'Software Engineer', 60000.00, '2020-01-15');

-- Query the list of employees in a department
SELECT Employees.Name, Employees.Position, Employees.Salary
FROM Employees
WHERE Employees.DepartmentID = 1;

-- Query the department information for a specific employee
SELECT Employees.Name, Departments.Name AS Department, Departments.Location
FROM Employees
JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID
WHERE Employees.EmployeeID = 101;
