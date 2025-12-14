# Step1: Split dataset into train dataset and test dataset
<img width="686" height="672" alt="image" src="https://github.com/user-attachments/assets/503a66c1-b712-4a6a-95af-e284fe242e95" />

# Step2: Use ADF to determine if it is stable.
I find the dataset is not stationary.     
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
I first perform seasonal differencing, then we test it again with ADF,  ```(p-value): 0.000000```.       
Then I draw a plot an autocorrelation plot to determine seasonality (using data after removing trends and seasonality).        
<img width="2140" height="1274" alt="image" src="https://github.com/user-attachments/assets/637c0be1-2d48-458d-add2-24381c3d7518" />   

# Step5: Train the ARMA model.
<img width="1418" height="1042" alt="image" src="https://github.com/user-attachments/assets/d3fc8cfe-fd72-4f86-bab6-5c245583d411" />

# Step6: Use  fitted model to predict passengers number
<img width="600" height="604" alt="image" src="https://github.com/user-attachments/assets/738c9ff6-a0e0-45c9-8b5e-1bfb6fb32b6b" />      
Draw a plot to compare the predicted values with the actual values.      
<img width="1428" height="707" alt="image" src="https://github.com/user-attachments/assets/a950c958-0fe9-4241-9e6b-c921d91926bc" />
Calculate the MAPE:  
<img width="2490" height="188" alt="image" src="https://github.com/user-attachments/assets/f233475a-1323-4bb8-a265-f38ae45e983f" />


