
# Single Variable Calculus Lab

In this lab, we will practice our knowledge of derivatives.  For this first section, you should be able to answer with an understanding of our definition of a derivative:

1. Our intuitive explanation that a derivative is the instantaneous rate of change of a function
2. Our mathematical definition that
$f'(x) = \frac{\Delta y}{\Delta x} =  \frac{f(x + h) - f(x)}{h}$
3. Our graphical understanding that a derivative at a given point equals the slope of the tangent line at a given point  

###  Applying our definition understandings

Let's start with our graphical understanding of derivatives.  Consider the graph below.

![](./tangentline.png)

The the blue line represents the function $f(x)$.  The orange line, labeled `trace 1`, is tangent to that line.  You are told that the orange tangent line can be represented by our classic formula for a line, $y = mx + b$ with the specific line $y = 3x + 12$.  In the below slot, write the derivative of the function $f(x)$ at the point of the tangent line.  For example write `derivative_of_graphed_function = 18` if you believe that is the derivative. 

> Hint, the answer should be a number.  Also, think about what the slope of the tangent line, $y = 3x + 12 $ equals.


```python
derivative_of_graphed_function = 'write answer here'
```

Now imagine that we have a new function, $f(x)$, and we again given a line tangent to the function $f(x)$ when $x = 3$.  We are provided with two points, `point_1` and `point_2`, which **lie along that line that is tangent to the function at $f(3)$ **.


```python
point_1 = {'x': 3.0, 'y': 5}
point_2 = {'x': 3.5, 'y': 7}
```

Now write a function `derivative_provided_tangent` that takes as arguments two points that lie tangent to a function at a given value of $x$.  The return value of `derivative_provided_tangent` is the function evaluated at that point.


```python
def derivative_at_x_value_provided_tangent(point_1, point_2):
    pass
```

For example, the when we execute this function below, it should return the derivative $f'(3)$.


```python
derivative_at_x_value_provided_tangent(point_1, point_2) # 4.0
```

Assume we are provided with two points, `point_3` and `point_4`, which **lie along that line that is tangent to the function at $f(4)$ **.  Ensure the function still works.


```python
point_3 = {'x': 4.0, 'y': 9}
point_4 = {'x': 4.5, 'y': 15}

derivative_at_x_value_provided_tangent(point_3, point_4) # 12.0
```

### From function to derivative

In this section we'll begin to build out a set of functions related to taking the derivative of a function.  Before we calculate derivatives of a function $f(x)$, we need to tackle the problem of expressing functions in code.  For example, how do we represent $f(x) = 2x^2 + 4x - 10 $ with code?  We want to write it in a way that allows us to easily figure out how the exponent of each term.

This is our technique: write the formula as a list of tuples.  Take the following function as an example: $$f(x) = 4x^2 + 4x - 10 $$

Here it is as a list of tuples:


```python
four_x_squared_plus_four_x_minus_ten = [(4, 2), (4, 1), (-10, 0)]
```

So each tuple in the list represents a different term in the function.  And the first element of the tuple is the term's constant and the second element of the tuple is the term's exponent.  Thus $4x^2$ translates to `(4, 2)` and  $-10$ translates to `(-10, 0)` because $-10$ equals $-10*x^0$.  We'll refer to this list of tuples as "list of terms", or `list_of_terms`.

Ok, so give this a shot. Write $ f(x) = 4x^3 + 11x^2 $ as a list of terms.  Assign it to the variable `four_x_cubed_plus`.


```python
four_x_cubed_plus = [('write', 'out'), ('your', 'answer')]
```

Now that we can represent $f(x)$ in code, let's write a Python function that can evaluate $f(x)$ at a specific value of $x$ and return that value, for example $f(3)$.  

Write a function called `output_at`, that when passed a `list_of_terms`, and a value of $x$, calculates the value of the function at that value of $x$.  For example, imagine we are using `output_at` to calculate $f(x) = 3x^2 - 11$.  Then `output_at([(3, 2), (11, 0)], 1)` should return $f(1) = 3*1^2 - 11 = -8$


```python
def output_at(list_of_terms, x_value):
    pass
```


```python
three_x_squared_minus_eleven = [(3, 2), (-11, 0)]
output_at(three_x_squared_minus_eleven, 1) # -8 
output_at(three_x_squared_minus_eleven, 3) # 16 
```

Now write a function, `df_dx` that calculates $\frac{\Delta f}{\Delta x}$ when provided as arguments, a list of terms named `function_as_list`, our `x_value` for the value of $(x)$ the derivative is evaluated at, and `delta`, which represents $\Delta x$.  Let's try this for $f(x) = 2x^3 + 7x $.  Round the result to three decimal places.


```python
two_x_cubed_plus_seven_x = [(2, 3), (7, 1)]
delta_value = .001
x_value = 2
```


```python
def df_dx(function_terms, x_value, delta):
    pass
```


```python
df_dx(two_x_cubed_plus_seven_x, x_value, delta_value) # 31.012
```

Ok, now that we written a Python function that calculates our `output_at` a value of $x$, and a Python function that calculates $\frac{\Delta f}{\Delta x}$ for a function at a value of $x$, we can begin to use these Python functions to plot functions, $f(x)$, and the related derivatives.

Write a function called `nonlinear_function_trace` that provided a `list_of_terms` as the first argument, and a list of `x_values` as the second argument, returns a dictionary that represents a trace of the function across those `x_values`.  This dictionary should have a key `x` that points to a list of `x_values` and a key of `y` that points to a list of values, equal to $f(x)$ for each of the provided `x_values`.

> Hint: Use the `output_at` function to calculate the correct value of `y`.


```python
def nonlinear_function_trace(function_terms, x_values):
    pass
```


```python
x_squared = [(1, 2)]
nonlinear_function_trace(x_squared, list(range(0, 3)))
# {'x': [0, 1, 2], 'y': [0, 1, 4]}

three_x_cubed_plus = [(3, 3), (-11, 0)]
nonlinear_trace = nonlinear_function_trace(three_x_cubed_plus, list(range(-4, 4)))
nonlinear_trace
# {'x': [-4, -3, -2, -1, 0, 1, 2, 3],
#  'y': [-203, -92, -35, -14, -11, -8, 13, 70]}

x_squared_trace = nonlinear_function_trace(x_squared, list(range(-3, 4))) or {}
# {'x': [-3, -2, -1, 0, 1, 2, 3], 'y': [9, 4, 1, 0, 1, 4, 9]}
```


```python
from graph import plot
from plotly.offline import iplot, init_notebook_mode
init_notebook_mode(connected=True)
plot([x_squared_trace])
```


<script>requirejs.config({paths: { 'plotly': ['https://cdn.plot.ly/plotly-latest.min']},});if(!window.Plotly) {{require(['plotly'],function(plotly) {window.Plotly=plotly;});}}</script>



<script>requirejs.config({paths: { 'plotly': ['https://cdn.plot.ly/plotly-latest.min']},});if(!window.Plotly) {{require(['plotly'],function(plotly) {window.Plotly=plotly;});}}</script>



<div id="9225bfbf-5aea-48f2-a367-c9985a22dc8e" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("9225bfbf-5aea-48f2-a367-c9985a22dc8e", [{}], {}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>


Ok, now that we have written a Python function that allows us to plot our list of terms, we can write a function that called `tangent_line_delta` can produce lines tangent to a provided function. We'll walk you through this one.  

Our `tangent_line_delta` takes as arguments `list_of_terms`, a value x called `x_value`, which is where our line should be tangent to our function, `line_length` as the length of our tangent line, and `delta` which is our $\Delta x$.

Our function `tangent_line_delta` returns a dictionary that represents a line of values of $x$.  The way it works is by using the `df_dx` function you wrote above to calculate the slope of the tangent line.  Once the slope of the tangent is calculated, we stretch out this tangent line by the `line_length` provided.  The beginning x value is just the midpoint minus the `line_length/2` and the ending $x$ value is midpoint plus the `line_length/2`.  Then we calculate our $y$ endpoints by starting at the $y$ along the function, and having them ending at `line_length/2*slope` in either direction. 


```python
def tangent_line_delta(list_of_terms, x_value, line_length = 4, delta = .01):
    pass
#     derivative_at = df_dx(list_of_terms, x_value, delta)
#     y = output_at(list_of_terms, x_value)
#     x_minus = x_value - line_length/2
#     x_plus = x_value + line_length/2
#     y_minus = y - derivative_at * line_length/2
#     y_plus = y + derivative_at * line_length/2
#     return {'x': [x_minus, x_value, x_plus], 'y': [y_minus, y, y_plus]}
```

One again, we encourage you to with the values of the function.  See that the line becomes more tangential as the value of delta approaches zero.


```python
tangent_at_five_trace = tangent_line_delta(x_squared, 2, line_length = 1, delta = .001) or {}
# {'x': [1.5, 2, 2.5], 'y': [2.0, 4, 6.0]}
plot([x_squared_trace, tangent_at_five_trace])
```


<div id="08ab535f-e8c0-464a-8bd8-ef4b2269ae6f" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("08ab535f-e8c0-464a-8bd8-ef4b2269ae6f", [{}, {}], {}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>

