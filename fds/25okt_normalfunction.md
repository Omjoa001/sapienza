# Normal equation
<sub>25okt</sub>

Todo: [Normal Equation in Linear Regression](https://www.geeksforgeeks.org/ml-normal-equation-in-linear-regression/#:~:text=Normal%20Equation%20is%20an%20analytical,a%20dataset%20with%20small%20features.)

The motive in Linear Regression is to minimize the cost function : <br> 
$J(\Theta) = \frac{1}{2m} \sum_{i = 1}^{m} \frac{1}{2} [h_{\Theta}(x^{(i)}) – y^{(i)}]^{2}$

Summary: Set of known (x,y) points. Find function $f(x)=ax+b$

The better the function fits the points, the more coorrelation between x and y. Our goal with regresseion is to find the line that minimizes the SSE (sum of squares of errors). The coorelation co-effictient varies between 0 and 1. In maximum positive correlation, we get 1 and with maximum negative we get -1. 

### Locally weighted regression
In Parametric learning algorithm we have a fixed set of parameters, where in our example in linear regression the parameter was a set of theta vectors. In non-parametric learning algorithm, parameters grow with the data.

In locally weighted regression you evaluate hypothesis $h$ at certain $Θ$ . There you ftit $Θ$ to minimize the $\sum(w^i)$. X and y are vectors of the same length. Every time you want to predict the value y of a new x you have to recalculate the new weights.

least squares: The cos -function has some assumptions, the values that we got as training values were given by a model that can justify our $w^i$ . There is going to be some error after we fit the line. This error is given by random noise. This noise is $y^i$ . We care about this because next we want to consider the likelihood of the parameters, which is equal to the probability of the training data that we have been given. This can be described with $L(Θ), P(y^{->}|x;Θ)$ .

We want to maximize the likelihood of our theta $Θ$ . We want to rather use the log likelihood, $log(Θ)$ . 


### Probability theory review.

For any events $A, B$ such that $P(B)≠0$ we define  <br>
$P(A|B):={P(A \bigcap B)\over{P(B)}}$

The probability of a patient being alcoholic A is $ P(A) = 0.05 $ . We know that the probability of $B$ is $ P(B) = 0.1$  where $B$ is that the patient has liver disease. But also among your patients with liver disease the probability of being alcoholic is $ P(A|B) = 0.07$ . The probability of $ P(B|A) = {{0.1 * 0.07}\over{0.05}} = 0.14$ . Here you assume that if a patient is alcoholic there is an increased risk of having liver disease.

Conditioned Bayes' Rule: given events $A,B,C$ <br>
$ P(A|B|C) = {P(b|a,c)P(a|c)\over{P(b|c)}} = {P(a|c)\over{P(b|c)}}={{P(a,b,c)}\over{p(c)p(b|C)}}=p(a|bc)$

Something useful, if you take n events, the joint probability can be the expressed as a product of conditionals.
$P(A_1\bigcap A_2 ... \bigcap A_3) $ <br>
$ P(A_n | A_n-1 \bigcap A_n-2 \bigcap $ ....)

