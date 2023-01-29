
**The total sales for each department per quarter i.e. “2nd Quarter totals: Electrical, £208,000”**

```pseudocode
DEPARTMENT-SALES-BY-QUARTER(A,d,m)
// A is a 2D array containing sales data by department
// d is the number of departments
// m is the number of months

// iterate departments
for i = 1 to d
	q2 = 0
	q3 = 0
	// iterate inner array of months
	for j = 1 to m
		if j = 1 or j = 2 or j = 3 then
			q2 = q2 + A[i].[j]
		else
			q3 = q3 + A[i].[j]
	
	print "Quarter 2, Department: " i " £" q2 ",000"
	print "Quarter 2, Department: " i " £" q3 ",000"



return D
```




**The name of the best and worst preforming department per quarter, with its respective monthly sales i.e. “2nd Quarter best: Kitchen, £65, 000, £67,000, £56,000” for the second quarter.**

```pseudocode
BEST-AND-WORST(A,d,m)
// A is a 2d array containing monthly sales figures by department
// d is the number of departments
// m is the number of months

q2dept = 0  //  best dept index for quarter 2
q3dept = 0  // best dept index for quarter 3
q2best = 0  // best monthly sales total for quarter 2
q3best = 0  // best monthly sales total for quarter 3
q2month = 0  // best month for quarter 2
q3month = 0 // best month for quarter 3

//iterate departments
for i = 1 to d
	q2 = 0
	q3 = 0
	// iterate inner array of months
	for j = 1 to m
		if j = 1 or j = 2 or j = 3 then //check which quarter the month is
			q2 = q2 + A[i].[j]
		else
			q3 = q3 + A[i].[j]
	// check if these quarterly totals are better than current best
	if q2 > q2best then 
		q2dept = i
		q2best = q2
		q2month = j
	if q3 > q3best then
		q3dept = i
		q3best = q3
		q3month = j

print "2nd Quarter best:" q2dept "," A[q2dept].[q2month]
print "3rd Quarter best:" q3dept "," A[q3dept].[q3month]
	
```

**The most effective month for each department (within a quarter) and its sales for that month, i.e. “3rd Quarter: Kitchen, September, £72,000; Electrical, August £104,000”**

```pseudocode
BEST-MONTH(A,d,m)
// A - 2D array containing monthly sales data by department
// d - number of departments
// m - number of months


//iterate departments
for i = 1 to d
	
	t2 = 0 //best q2 month sales total
	t3 = 0 //best q3 month sales total
	b2 = 0 //best q2 month
	b3 = 0 //best q3 month
	
	// iterate inner array of months
	for j = 1 to m
		if j = 1 or j = 2 or j = 3 then 
			if A[i].[j] > b2 then
				t2 = A[i].[j]
				b2 = j
		else
			if A[i].[j] > b3 then
				t3 = A[i].[j]
				b3 = j
	print "2nd Quarter: Department " i " month " b2 " total £" t2
	print "3rd Quarter: Department " i " month " b3 " total £" t3

```


**Given the total sales for each quarter, calculate the tax that needs to be paid at 17%**

```pseudocode
TAX-CALC(A,d,m)
// A - 2D array containing monthly sales data by department
// d - number of departments
// m - number of months


//iterate departments

q2 = 0 //total sales quarter 2
q3 = 0 //total sales quarter 3
t2 = 0.00 //tax to be paid quarter 2
t3 = 0.00 //tax to be paid quarter 3
TAX_RATE = 0.17

for i = 1 to d
	// iterate inner array of months
	for j = 1 to m
		if j = 1 or j = 2 or j = 3 then 
			q2 = q2 + A[i].[j]
		else
			q3 = q3 + A[i].[j]
		

t2 = q2 * TAX_RATE
t3 = q3 * TAX_RATE
print "Tax to be paid Quarter 2: " t2 
print "Tax to be paid Quarter 3: " t3
```

**Given the average sales for each department across the last reported quarter, provide a new sales target for each department with an increase of 12%**

```pseudocode 
SALES-TARGET(A,d,m)
// A - 2D array containing monthly sales data by department
// d - number of departments
// m - number of months

TARGET_PERCENTAGE_RATE = 0.12
MONTHS_PER_QUARTER = 3


for i = 1 to d
	t = 0  // department sales target
	
	// iterate inner array of months
	s = 0  //department total sales
	v = 0  //department average sales
	for j = 1 to m
		if j = 4 or j = 5 or j = 6 then 
			s = s + A[i].[j]
	t = (s / MONTHS_PER_QUARTER) * TARGET_PERCENTAGE) + s
	print "Sales target for department " i " is £" t ",000" 	
```


