# CPO Price Prediction using Simulated Annealing-based Support Vector Regression

## Introduction
The study use a metaheuristic algorithm, called Simulated Annealing (SA) to optimize the hyperparameter of the Support Vector Regression (SVR) model. 

### Support Vector Regression
Support vector regression (SVR) is an extension of the support vector machine (SVM) applied to regression problems. Linear, polynomial, radial basis function (RBF), and sigmoid kernels are the most commonly used kernels in an SVM implementation. There is no direct way to determine the best kernel choice for a specific data pattern. According to Ojemakinde (2006), without prior knowledge about the data, the RBF kernel is the preferable choice justified by some valid reasons. First, it requires less tuneable hyperparameters than polynomials. RBF also has fewer numerical difficulties since the kernel value (𝛾) ranges from 0 to 1, whereas the range of these values of the polynomial kernel can fall between 0 and ∞. Besides, although the sigmoid kernel is successfully applicable, it is not always fulfilling the requirement for an SVR kernel, called Mercer’s condition. The sigmoid kernel is also similar to the RBF kernel when the kernel width is small. In addition, Ali Alahmari (2020) and Saadah et al. (2021) revealed that SVR with RBF kernel demonstrated an outstanding prediction performance in price prediction problems.

For any kernel type, the SVR model complexity can be affected by the values of 𝐶 and 𝜀. In this project, the intention is applying the RBF kernel for CPO price forecasting. Therefore, the tuneable hyperparameters of the RBF-SVR model are C, ε, and γ. Simulated annealing (SA) will be used to find the near optimal solutions for these hyperparameters to improve the prediction performance.

### Simulated Annealing
The simulated annealing (SA) algorithm is an iterative improvement algorithm. It uses a random search, which always accepts changes (solutions) that improve the objective function but sometimes also keeps some changes that are not ideal in the search process based on the acceptance probability function. SA parameters that impact the result of hyperparameter tuning include cooling factor (𝛼), number of iterations, initial temperature (_T_<sub>0</sub>) and minimum temperature  (_𝑇_<sub>min</sub>).

According to Fischetti and Stringher (2019), 𝑇 can be updated using a simple formula 𝑇 = 𝛼 × 𝑇, with cooling factor 𝛼 ∈ (0,1) such that 𝛼 ∈ (0.7, 0.8) when cooling is applied after several SA iterations with a constant 𝑇. Hence, it would be ideal to take an average of the two boundaries, 0.7 and 0.8, which is 0.75.

Note that SA is an iteration-intensive algorithm where the number of iterations at any given temperature will affect the duration and the quality of the obtained solution. The number of iterations needed to achieve global optima depends on the size of the problems, as the number of iterations might be as large as millions. However, Martinez-Rios and Frausto-Solis (2012) were able to use SA with only 100 iterations in solving a nondeterministic polynomial-time complete (NP-complete) problem, which is the “Boolean Satisfiability problem”. Thus, we consider using 100 iterations in hyperparameter tuning is worthwhile as this process might involve the search space of a million numbers.

Finally, choose both initial (_T_<sub>0</sub>) and minimum (_T_<sub>min</sub>) temperatures wisely since they affect the acceptance probability, which impacts the overall tuning result. _T_<sub>0</sub> should be large enough to make the initial acceptance probability closer to 1, and _T_<sub>min</sub> should be much lower so that the acceptance probability decreases gradually throughout the annealing process. Fischetti and Stringher (2019) chose _T_<sub>0</sub> = 1 and considered a temperature reduction of 3 to 5 times, which has reduced the acceptance probability low enough. Therefore, we decided to set _T_<sub>0</sub> = 100 and _T_<sub>min</sub> = 30 (achieved after five times temperature reductions) for this project.

### Google Colab

Use Google Colab for faster execution of the code https://colab.google/


