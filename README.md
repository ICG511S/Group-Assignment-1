# Group Assignment 1

Imagine you are hired by retail giant Shoprite to design them some software for their daily operations. The company needs software that enables them to sell their products, keep track of stock, and receive some prompts from the system to reorder some new item if the stock runs low. Upon receiving new stock, the managers should be able to add new stock before selling begins. Shoprite also needs the same software to be able to manage their employees, particularly on the hours worked, which will later be used to calculate the salary depending on the job grade of the employee. The system should also track whether an employee is permanently employed or is on contract. Kindly use the marking rubric below to design software that Shoprite can use. (Note: Students are allowed to expand the scenario as long as it remains in the confinement of retail operations. Deliberations on the scenario can be done in the tutorial class or students can interview people working in retail to understand some daily operations involved.)
**#######################################################################################**
**################# This may look like pseudocode but it is just the outline of the modules #################**
**#######################################################################################**
**Modules**

**1. Login**
1. Verify userID and passcode and set userID and passcode variable
2. Sets the variable userPermission from userRecords.permission (1=Sales, 2=Senior Sales 3=Operational Management, 4=Middle Management, 5=Executive, 6=System Administrator) *A higher permission set can access all below permissions E.g. Set 3 can access 1,2 and 3*
3. Create record in logRecords.(UserID, date, time and type) = (userID, get currentDate, get currentTime, IN)
4. If userPermission >=3 and if sum (select all from stockRecords where stockRecords.amountInStock <                        - stockRecords.threshold > 0) then stock-low notification. If userPermission >= 3 and getCurrentDate(day) = 24 then payday - notification. If userPermission >= 3 and getCurrentDate(day) = 28 then stocktake notification.
5. Start **Main Menu**

**2. Logout**
1. Set userPermission = 0
2. Create record in logRecords(UserID, date, time and type) = (userID, get currentDate, get currentTime, OUT)
3. End program

**3. Main Menu**
1. If userPermission <= 3 show Sale and Logout, else if userPermission >= 3 show Sale, Stock, Human Resources and logout 
2. If select logout then start **2. Logout** else if select sale then start **4. Sale** else if select stock then start **5. Stock** else if select human resources then start **6. Human Resources**

**4. Sale**
1. Input itemID
2. Input loyaltyID
3. Output total
4. Input amount received
5. Output change and receipt
6. Subtract items purchased from inventory
7. Restart or go to **3. Main Menu**

**5. Stock**
1. If select stocklist then select all from stockRecords
2. If select edit then edit else if select stocktake then stocktake

**6. Human Resources**
1. If select employee list then employee-list else if select payroll-list
2. Employee-list: Add new employee to userRecords and employeeRecords Database, Edit existing (edit userRecords and  or employeeRecords) or delete record userRecords and employeeRecords
3. Payroll-list: select all from payrollRecords where payrollRecords.month = getCurrentMonth
