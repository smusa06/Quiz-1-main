# Quiz 1 main


3) Use PROC CONTENTS to find out some information about this dataset. How many
observations does the dataset have? How many variables does the dataset have?;

proc contents data=quiz1.quiz1_data;
run;

Answer : this dataset has 1150 observations and 7 variables.


4) 4. Use PROC FREQ to provide information about the variable diabetes. If this variable represents those individuals in the dataset with diabetes, what proportion of people in the dataset have diabetes? (provide the frequency table with your answers).
 
  
* Answer: 31 people making 2.7% of the population have diabetes in this dataset.




4) 4. Use PROC FREQ to provide information about the variable diabetes. If this variable represents those individuals in the dataset with diabetes, what proportion of people in the dataset have diabetes? (provide the frequency table with your answers).
 
  
* Answer: 31 people making 2.7% of the population have diabetes in this dataset.

 5. Use PROC UNIVARIATE to provide information about the variable X1.
a) What are the mean and standard deviation of X1?
Mean of X1 =1.174917
Stan dev of X1 =0.98058


b) Produce a frequency histogram of X1
(provide with your answers)
 



6. Create a temporary copy of the quiz1 dataset called work.quiz1.;
*The remainder of the questions involve working with the work.quiz1 dataset.

data work.quiz1;
set quiz1.quiz1_data;
run;


7. a) Create a new variable called mean_V1 that is the mean of X1,X2 and X3 using mathematical operators.
data work.quiz1;
	set quiz1.quiz1_data;
	mean_V1= (X1+X2+X3)/3;
	run;



b) Create a new variable called mean_V2 that is the mean of X1,X2 and X3 using a SAS function.
data work.quiz1;
	set quiz1.quiz1_data;
	mean_V2= mean(X1,X2,X3);
	run;



8. Consult_dt and Surgery_dt are SAS dates. Create a new variable called wait_time that calculates the time in days between consult and surgery.
data work.quiz1;
	set quiz1.quiz1_data;
	wait_time = Surgery_dt-Consult_dt;




	run;
*9.  Create a new variable called X2_high which has a value of 1 if X2 is greater than or equal to the mean of X2 and 0 otherwise 
(you can find the mean of X2 using PROC UNIVARIATE).

data work.quiz1;
	set quiz1.quiz1_data;
	X2_high = X2;
	if X2 => 11.0460406 then X2_high=1;
	else X2_high=0;
	run;
	*mean(X2)=11.04604;
	
proc univariate data=quiz1.quiz1_data;
var X2;
run;
*code to determine mean of X2 value;


10.a)Use PROC UNIVARIATE to find out the mean values of the variables of mean_V1,and mean_V2, and the median, minimum and maximum values for wait_time.
	
proc univariate data=work.quiz1;    
var wait_time;
run;
Median of wait_time =52.0
Maximum value of wait_time   = 99
Minimum value of wait_time = 0

proc univariate data=work.quiz1;    *Mean=12.73950;
var mean_V1;
run;

Mean of Mean_V1= 12.73950;

proc univariate data=work.quiz1;       *Mean=12.73950;
var mean_V2;
run;

Mean of Mean_V2= 12.73950;



10b) Use PROC FREQ to create a 2x2 frequency table for X2_high vs. diabetes (provide frequency table with your answers).
 

proc freq data= work.quiz1;
table X2_high * diabetes;
run;


