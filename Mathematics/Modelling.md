Modelling is the process of developing an abstract representation of a system. This maps the domain of the problem to model's output. There are two main types of models, these are:
- **Mathematical models** which through the use of a **governing equation** describe how an unknown variable changes given its inputs. 
- **Computational models** which use an algorithm to find how a system changes given input variables.

# Error
During the process of modelling their is a variety of possible sources of error. The three types of error which are common within modelling are:
- **Modelling error** which arises from the lack of ability of the model to represent the realities.
- **Data errors** which arise from inaccuracy within measurements or computations which propagate errors.
- **Computational error** which arises from truncations and rounding causing error.

Error can be calculated as **absolute error** by comparing the approximate value to the real value. Alternatively **relative error** is found by subtracting the true value by the error and dividing the result by the true value. ## Test

Given an error calculated as $\text{Total Error}=\tilde{f}(\tilde{x})-f(x)$, then the computational error can be found as $\tilde{f}(\tilde{x})-f(\tilde{x})$ and data error as $f(\tilde{x})-f(x)$.

**Forward error** is calculated as the difference between the **computed** and **true** value. This means absolute and relative error are examples of forward error. **Backward error** is the discrepancy in the input that would lead to the observed discrepancy in the output.

The **sensitivity**  is a qualitative statement of propagated data error, while **conditioning** is the quantitative measure of sensitivity.  
