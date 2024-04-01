# Homework 1 

First Homework Results for Basic Attacks

The code can be found in the repository [code](/code).

##  Poisoning attacks

<b>Task:</b> In the lesson, you have learned about BadNetsAttack in several cases, include for
traffic sign recognition. Based on the sample codeWeek4-Badnet.ipynbin Demo code,
please reproduce one of the results.

a. Insert a trigger to a number 6 In Mnist dataset(30pts)

b. What is the best size in pixels for the trigger(10pts)?


To check the hypothesis about the best size in pixels for the trigger, it was decided to
create three different poisoned marks:

- Big
- Small
- Original (from the teacher's code)
  
After running the code with class "6" we get the following results:

![result](/img/res_6.png)


| Sample | Size in pixels | Confidence | Number of epochs | Accuracy Before | Accuracy After |
| --- | --- | --- | --- | --- | --- |
| Original | 9 | 1.00 | 10 | 89.34 | 0.94 |
| Big | 21 | 1.00 | 10 | 71.48 | 9.35 |
| Small | 4 | 1.00 | 10 | 89.45 | 0.7 |

## Model inversion attack

<b>Task:</b> In the lesson, you have learned about adversarial attacks. Based on the sample
code Week4-Model-Inversion-Attack.ipynb, please reproduce the results for one case
and answer the following question.

a. What is the meaning of minimum over all maximum class gradient? Is a big value of the class gradient better or worse? (20pts)

b. What is the Wall time and how to reduce it? (20pts)

<b>Answer a:</b>

Our main goal is to achieve class poisoning. At the same time, we want to make minimal changes. In that case 
it’s necessary to select the parameters that help attacker to achieve the result.

Thus, the dependence of the class gradient is directly proportional to the change in the
model output. If the value of the class gradient is high, then the more significantly model
will react to changes in the data supplied to the input, even minor ones. Here minor
changes may be that are invisible to the human eye. In this work, for us as attackers, the
higher the gradient, the easier it is to provide an attack.


<b>Answer b:</b>

Wall time - is the amount of time that a program takes to run from start to end, including
all stages of the pipeline.

Speaking in this context, of the time reducing we can make it in the several ways:

  − We can optimize the input data by reducing its dimensionality or send it to the
  preprocessor. But in this case, it will be necessary to develop a tool that can
  process data faster. Compare to the way it was originally.
  
  − We can simply take more powerful computing resources, which will cost
  additional money.
  
  − Early it’s written about class gradients before, so we can calculate gradients for a
  set of input data or for classes in advance.
  
  − We can also shorten our model by simplifying the architecture or computation
  model. Which can help in a situation where we cannot manipulate the input
  data.


## Hidden attack

<b>Task:</b> 

In the demo code Week4-Poisoning-attacks-2.ipynb , I show you how to hide the
person with a trigger. In this assignment, please try to increase percent_poison=0.5 and
percent_poison=0.1, explain

1. What is the retrieved result compared to the setting of percent_poison=1.0?
(10pts)

3. Use another trigger type (replace htbn.png to the other pattern) and show the
result(10pts)

We are experimenting with four different types of attacks and the percent_poison
parameter (0.1; 0.5; 1.0):

  − BadDet Regional Misclassification Attack
  
  − BadDet Global Misclassification Attack
  
  − BadDet Object Generation Attack
  
  − BadDet Object Disappearance Attack

Trigger for experiments:

![tg_1](/img/1.png)

<b>Answer for 2:</b>

Here is another trigger type for new experiments. The difference between the previous
one is the colors and the way they represent. 

Pixel density is different:

![tg_2](/img/2.png)
