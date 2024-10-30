java cBUSS6002 Assignment
Semester 2, 2024
Instructions
• Due: at 23:59 on Friday, October 25, 2024 (end of week 12).
• You must submit a written report (in PDF) with the following filename format, replacing
STUDENTID with your own student ID: BUSS6002 STUDENTID.pdf.
• You must also submit a Jupyter Notebook (.ipynb) file with the following filename format,
replacing STUDENTID with your own student ID: BUSS6002 STUDENTID.ipynb.
• There is a limit of 6 A4-pages for your report (including equations, tables, and captions).
• Your report should have an appropriate title (of your own choice).
• Do not include a cover page.
• All plots, computational tasks, and results must be completed using Python.
• Each section of your report must be clearly labelled with a heading.
• Do not include any Python code as part of your report.
• All figures must be appropriately sized and have readable axis labels and legends (where
applicable).
• The submitted .ipynb file must contain all the code used in the development of your report.
• The submitted .ipynb file must be free of any errors, and the results must be reproducible.
• You may submit multiple times but only your last submission will be marked.
• A late penalty applies if you submit your assignment late without a successful special con sideration. See the Unit Outline for more details.
• Generative AI tools (such as ChatGPT) may be used for this assignment but you must add a
statement at the end of your report specifying how generative AI was used. E.g., Generative
AI was used only used for editing the final report text.
• Hint! It is highly recommended that you finish the week 10 tutorial before starting this
assignment.
1
Description
One of the UN Sustainable Development Goals is ‘climate action’ (goal 13). In this assignment,
you are conducting a study that compares the predictive performance between three families of
basis functions: polynomial, piece-wise constant, and piece-wise linear, for a linear basis function
(LBF) model designed to predict the global surface air temperature. The aim is to investigate
which family of basis functions is most suited for modelling the relationship between time and
temperature.
You are provided with the ERA5 surface air temperature dataset, which is widely used in
climate research, weather forecasting, and environmental monitoring. The dataset contains 1,017
observations of monthly surface air temperature in degrees Celsius (temp) from January 1940 to
September 2024. It also contains the year (year) and month (month) for which the temperature
is observed. A scatter plot of the dataset is shown in Figure 1.
Figure 1: ERA5 surface air temperature from January 1940 to September 2024.
The specific LBF model being considered in your study is given by
y = u
⊤α + ϕ(x)
⊤β + ε,
where y is the surface air temperature, x is year, and ε is a random noise; u := [u2, . . . , u12]
⊤ is a
binary vector of dummy variables, with ui = 1 if y is observed in month i and u = 0 otherwise;
ϕ(x) denotes the vector of basis function values; the parameter vectors are α and β. Three families
of basis functions are considered for computing ϕ(x); the first family is the set of polynomial basis
functions ϕ(x) := [1, ϕ1(x), . . . , ϕp(x)]⊤, with
ϕi(x) := x
i
.
The second family is the set of piece-wise constant basis functions ϕ(x) := [1, γ1(x), . . . , γk(x)]⊤,
with
γi(x) := I(x > ti),
where I(x > ti) is an indicator function defined by
I(x > ti) := ( 1 if x > ti
0 if x ≤ ti
.
2
The break points {ti}
k
i=1 are calculated according to
ti
:= xmin +
i(xmax − xmin)
k + 1
, (1)
where xmin and xmax denote the smallest and largest observed values of x, respectively. The third
family is the set of piece-wise linear basis fun代 写BUSS6002、Python
代做程序编程语言ctions ϕ(x) := [1, x, λ1(x), . . . , λk(x)]⊤, with
λi(x) := (x − ti)I(x > ti),
where ti
is given by Equation (1).
Before comparing the three basis function families, you must set the degree p for the polynomial
model, and the number of break points k for the piece-wise constant and piece-wise linear models.
The hyperparameter value for each basis function family should be selected using a validation set,
by minimising the validation mean squared error (MSE).
For the polynomial model, the optimal value of p should be selected by exhaustively searching
through an equally-spaced grid from 1 to 10, with a spacing of 1:
P := {1, 2, . . . , 10}.
For the two piece-wise models, you should select the optimal values of k by exhaustively searching
through another equally-spaced grid from 1 to 30, with a spacing of 1:
K := {1, 2, . . . , 30}.
Once the optimal values of the hyperparameters are chosen for all basis function families, you
will be able to compare the predictive performance between the three using a test set (i.e., by
comparing the test MSE between the three optimally selected models).
3
Report Structure
Your report must contain the following four sections:
Report Title
1 Introduction (0.5 pages)
– Provide a brief project background so that the reader of your report can understand
the general problem that you are solving.
– Motivate your research question.
– State the aim of your project.
– Provide a short summary of each of the rest of the sections in your report (e.g., “The
report proceeds as follows: Section 2 presents . . . ”).
2 Methodology (2 pages)
– Define and describe the LBF model.
– Define and describe the three choices of basis function families being investigated.
– Describe how the parameter vectors α and β are estimated given the hyperparameter
value. Discuss any potential numerical issues associated with the estimation procedure.
– Describe how the hyperparameter value can be determined automatically from data (as
opposed to manually setting the hyperparameter to an arbitrary value).
– Describe how the performance of the three families of basis functions is compared given
the optimal hyperparameter value.
3 Empirical Study (2.5 pages)
– Describe the datasets used in your study.
– Present (in a table) the selected hyperparameter value for each basis function family.
– Describe and discuss the table of selected hyperparameters.
– Visually present (using plots) the predicted response values for each basis function
family in the test set.
– Describe and discuss the plots of predicted values.
– Present (in a table) the test MSE values for each basis function family.
– Describe and discuss the table of test MSE values.
– Report the temperature forecasts for October, November, and December of 2024 given
by the model with the smallest test MSE. Include a brief description of how these
forecasts are obtained.
4 Conclusion (0.5 pages)
– Discuss your overall findings / insights.
– Discuss any limitations of your study.
– Suggest potential directions of extending your study.
4
Rubric
This assignment is worth 30% of the unit’s marks. The assessment is designed to test your compu tational skills in implementing algorithms and conducting empirical experiments, as well as your
communication skills in writing a concise and coherent report presenting your approach and results.
The mark allocation across assessment items is given in Table 1.
Assessment Item Goal Marks
Section 1 Introduction 4
Section 2 Methodology 10
Section 3 Empirical Study 16
Section 4 Conclusion 3
Overall Presentation Clear, concise, coherent, and correct 5
Jupyter Notebook Reproducable results 2
Total 40
Table 1: Assessment Items and Mark Allocation
5

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
