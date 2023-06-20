# -Vasicek-Model-Calibration
Calibrating the Two-Factor Vasicek Model (N2 Model) using historical Treasury spot rate data. The objective is to identify the constant parameters and state variables that best fit the model to the given historical data.  involves an iterative algorithm and subsequent analysis of the time series properties of deviationsbetween the actual spot rates and the model's predicted rates.

Please go through the "questions asked" to understand what all I did in depth. A brief is given below
As park of my Fixed income assignment I implemented the following steps:

First, I began with an in-depth analysis of the provided spreadsheet containing 650 weeks of historical Treasury spot rate data. Each week's spot rates were expressed in percentage form for maturities of 0.25, 2.00, 3.00, 5.00, 7.00, and 10.00 years. After converting these percentages into decimal form, I was ready to commence the calibration of the Two-Factor Vasicek Model, also known as the N2 Model.

In this task, my goal was to solve for the six parameters of the N2 Model: kappaX, thetaX, sigmaX, kappaY, thetaY, and sigmaY. Additionally, I had to solve for the state variables Xt and Yt, which fluctuate over time and hence would have different values for each of the 650 weeks. This task entailed finding the best fit for a total of 1306 variables against the historical data.

Having recalled the formulation of a zero-coupon bond's price in the Vasicek Model, I was able to use this knowledge to proceed. I understood that the spot rate for a zero-coupon bond with maturity T could be written as a linear equation in Xt and Yt, given the six parameters and a value of T.

Next, I had to calibrate the model using a multi-step algorithm. I started by selecting an initial set of the six parameters. Then, I assumed that the N2 Model exactly fitted the 0.25 and 10.00-year spot rates for the first week. I identified these rates as r0.25 and r10.00, which resulted in two linear equations that allowed me to find X1 and Y1.

After finding X1 and Y1, I employed the N2 Model to calculate the model values of the other four spot rates for the first week (2-, 3-, 5-, and 7-year spot rates). I computed the squared difference between the actual and model-implied spot rates for each of these four rates, giving me four squared differences for the first week.

I then replicated this process for all 650 weeks. This iterative method provided the state variable values Xt and Yt for each week, along with a collection of 650×4 squared differences. Summing these squared differences allowed me to score each choice of parameters.

To identify the optimal parameters, I returned to the start of the algorithm and chose different parameters. I continued this process until I found the set of parameters that yielded the smallest score. As a simplifying assumption, I set kappaY to 0, which reduced the optimization to just five parameters. After finding the optimal parameters, I had successfully calibrated the N2 Model and obtained the corresponding state variables Xt and Yt for each of the 650 weeks.

Having completed the calibration, I graphed the values of Xt and Yt, and checked the sample moments against those implied by the risk-neutral parameter estimates. Finally, I analyzed the time series properties of deviations between the spot rates and the fitted model. This step allowed me to evaluate the convergence rate of the deviations between the 2-, 3-, 5-, and 7-year spot rates and the N2 Model-implied rates. From this, I inferred potential profitability of term structure trading strategies based on the N2 Model.
