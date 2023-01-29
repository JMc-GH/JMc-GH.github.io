```java
import java.util.HashMap;
	

public class Quarterly_Report {

		// this array holds the sales data
		// the outer array is departments
		// the inner array is monthly sales
		private int[][] sales = {
				{67,63,78,78,104,103}, 	// Electrical
				{65,67,56,45,56,72},	// Kitchen	
				{63,63,65,71,73,69},	// Bathroom
				{18,24,22,19,17,16},	// Soft Furnishings
				{16,23,21,19,20,19}};	// Accessories
		
		
		// HashMap contains human-sensible names for departments
		private HashMap<Integer,String> deptName = new HashMap<>();
		
		//constants: 
		private final int DEPTS = 5;
		private final int MONTHS = 6;
		private final int MONTHS_PER_QUARTER = 3;
		
		//setable attributes common to all instances
		static double TAX_RATE = 0.17;
		static double SALES_TARGET_INCREASE = 0.12;
		
		
		public Quarterly_Report () {
			
			// Set up the department names for output purposes later
			deptName.put(0, "Electrical");
			deptName.put(1, "Kitchen");
			deptName.put(2, "Bathroom");
			deptName.put(3, "Soft Furnishings");
			deptName.put(4, "Accessories");
			
		}
		
		
		public void setSalesData(int[][] newData) {
			
			//validate array has correct dimensions
			if (newData.length !=DEPTS || newData[0].length !=MONTHS ) throw(new Error("Array dimensions incorrect: should be 5 depts x 6 months"));
			
			// all ok then set it
			sales = newData;
		}
		
		
		public void departmentSalesByQuarter() {
			
			/*
			 *	1: The total sales for each department per quarter i.e. “2nd Quarter totals: Electrical, £208,000”
			*/
			
			int q2 = 0; // Q2 total sales
			int q3 = 0; // Q3 total sales
			
			//output title header
			System.out.println("TOTAL SALES BY DEPARTMENT");
			System.out.println("=========================");
			
			//iterate departments
			for (int i = 0;i < DEPTS;i++) {
				q2 = 0;
				q3 = 0;
				//iterate months
				for (int j = 0;j < MONTHS;j++) {
					if (j == 0 || j == 1 || j == 2)  //test which quarter the current month is in 
						q2 += sales[i][j];		// add sales to running total for quarter
					 else 
						 q3 += sales[i][j];
					}
			System.out.println("Q2 -- " + deptName.get(i) + " -- £" + q2 * 1000);
			System.out.println("Q3 -- " + deptName.get(i) + " -- £" + q3 * 1000);
				}
			
			};
		
		public void calculateTax() {
			
			/*
			 * 4.	Given the total sales for each quarter, calculate the tax that needs to be paid at 17%.
			 */
			
			if (TAX_RATE > 1.0 || TAX_RATE < 0.0) throw (new Error("Tax rate must be between 0 and 1"));
			
			int q2 = 0; //total sales quarter 2
			int q3 = 0; //total sales quarter 3
			double t2 = 0.00; //tax to be paid quarter 2
			double t3 = 0.00; //tax to be paid quarter 3
			
			
			for (int i = 0;i < DEPTS;i++) {			//iterate departments
				for (int j = 0;j < MONTHS;j++) { 	// iterate months
					if (j == 0 || j == 1 || j == 2) 
						q2 += sales[i][j];			// add to tally for this quarter
					 else 
						q3 += sales[i][j]; 
				}
			
			}
			t2 = q2 * TAX_RATE;
			t3 = q3 * TAX_RATE;
			
			System.out.println("TAX DUE");
			System.out.println("=======");
			System.out.println("Tax Q2 -- £" + t2 * 1000);
			System.out.println("Tax Q3 -- £" + t3 * 1000);
		}

		
		public void getSalesTarget() {
			
			/*
			 * 5. 	Given the average sales for each department across the last 
			 * 		reported quarter, provide a new sales target for each department with an increase of 12%
			 */
			if (SALES_TARGET_INCREASE > 1.0 || SALES_TARGET_INCREASE < 0.0) throw (new Error("Tax rate must be between 0 and 1"));
			
			double t;   //department sales target
			int s;	// department total sales
		
			
			System.out.println("SALES TARGETS");
			System.out.println("=============");
			
			
			for (int i = 0;i < DEPTS;i++) {
				
				//reset for next department
				t = 0;s = 0;
				
				for (int j = 0;j < MONTHS;j++) {
					if (j==3 || j==4 || j==5)
						s += sales[i][j];
				}
				t = ((s / MONTHS_PER_QUARTER) * SALES_TARGET_INCREASE) + s;
				System.out.println(deptName.get(i)+ " --  £" + t * 1000); 
			}
		}
			
		public static void main(String[] args) {
			
			// Test with default dataset
			Quarterly_Report testReport = new Quarterly_Report();
			
			testReport.departmentSalesByQuarter();
			System.out.println();
			
			testReport.calculateTax();
			System.out.println();
			
			testReport.getSalesTarget();
			System.out.println();
			
			// Test validation with new dataset
//			Quarterly_Report newReport = new Quarterly_Report();
//			
//			int[][] newSales = {
//					{67,63,78,78,104,103}, 	// Electrical
//					{65,67,56,45,56,72},	// Kitchen	
//					{63,63,65,71,73,69},	// Bathroom
//					{18,24,22,19,17,16},	// Soft Furnishings
//					{16,23,21,19,20,19}};	// Accessories
//			
//			newReport.setSalesData(newSales);
//			
//			newReport.departmentSalesByQuarter();
//			System.out.println();
//			
//			newReport.calculateTax();
//			System.out.println();
//			
//			newReport.getSalesTarget();
//			System.out.println();
		}
}


```
