# Step1: Split dataset into train dataset and test dataset
<img width="686" height="672" alt="image" src="https://github.com/user-attachments/assets/503a66c1-b712-4a6a-95af-e284fe242e95" />

# Step2: Use ADF to determine if it is stable.
We test and find the dataset is not stationary.     
<img width="1092" height="120" alt="image" src="https://github.com/user-attachments/assets/e36af9bb-f458-4554-9678-bc8aeff760d9" />

# Step3: Use difference to remove treand
<img width="734" height="232" alt="image" src="https://github.com/user-attachments/assets/f673fe3b-4463-4cfc-8e84-0d8dcccfbb1f" />       

# Step4: 
Observe the ACF curve in the graph:      
First peak: The curve shows a very high autocorrelation coefficient (around 0.8, or at least one of the highest peaks) near Lag = 12.      
Second peak: The curve shows another peak near Lag = 24.         
Third peak: The curve shows another peak near Lag = 36.       
Since 12 * 2=24, 12 * 3=36, this strongly suggests that the data has a seasonality with a period of m=12.   
<img width="2124" height="1284" alt="image" src="https://github.com/user-attachments/assets/3424796d-3f10-4e4d-9144-d1c33f067f51" />      
So I use ```df['Seasonal Difference'] = df['Difference'] - df['Difference'].shift(12) ```     
I first perform seasonal differencing, then we test it again with ADF, and plot an autocorrelation plot to determine seasonality (using data after removing trends and seasonality).     

