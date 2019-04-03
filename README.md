# kb-anonimity-For-Privacy-Preserving-in-Test-Data
A Python implementation of kb-anonimity algorithm for preserving privacy in test data. We provide different implementations, you can choose
one by passing the corresponding input parameters.

## Description
kb-anonimity is an anonymization algorithm that acts on test data. The main point which users must focus on is the trade off between privacy
and behaviour preservation. This means that we have:
<ul>
  <li>A program to test</li>
  <li>A raw dataset to feed our program</li>
</ul>

We aim at building an anonymized dataset to be given to someone who is going to test the program. Since we are choosing between behaviour
and privacy preservation, there exist different techniques to achieve different results. In this project you will find two main implementations 
that are called:

<ul>
  <li>Same Path - No Field Repeat</li>
  <li>Same Path - No Tuple Repeat</li>
</ul>

The term "behaviour" refers to the path through conditional branches that the execution of a program follows on a single tuple.

## Implementation Notes

We provide an example dataset:

<i>https://archive.ics.uci.edu/ml/datasets/Absenteeism+at+work</i>

In order to use a different dataset, the user has to change different values. For the sake of simplicity we grouped all the elements to be changed inside specific files (function_to_test, user_variables) that are already written for the example dataset and that can be used as a guide.
The algorithm works on numerical attributes, we recommend to normalize floating point values to integer ones to aviod roundings. Categorical fileds that are saved as strings can be turned into numbers.

For what concerns the program to test, we provide also a simple example function which is again in the files above. As it can be noticed, 
if the user wants to write his own program he needs to label all the conditional branches in the way it is done in the example.

The output dataset is provided in <i>.csv</i> format.

## Input Parameters and User Defined Values

Here you can find a detailed list of the input parameters and the value that the user must change to change dataset/program.

Program Input
<ul>
  <li>Dataset Name</li>
  <li>K: Level of anonymization. That is the least accepted cardinality for a given bucket</li>
  <li>Option: "pt" or "pf". That is how much privacy we want to preserve </li>
</ul>

User Defined Variables
<ul>
  <li>Number of conditions inside the test program</li>
  <li>Cardinalities of the attributes involved in conditional branches</li>
  <li>Attributes for which we allow a relaxed privacy. That is if the input option is "pf" and it is not achievable we can relax the constraints on the given fields</li>
</ul>

What the algorithm set for you
<ul>
  <li>The attribute whose domain has the highest cardinality</li>
  <li>The maximum number of iteration to the highest cardinality so that only CardinalityException will be raised</li>
  <li>Relaxed privacy dictionary is modified automatically by setting to 0 the field whose domain has the highest cardinality. In order to achieve a minimum level of privacy preservation at least a field must have this value set to 0</li>
</ul>

## Considerations on Constraints
We implemented a constraint generation and a constraint solver components. The second one acts in a very easy way, i.e. it generates new values randomly according to the domain of the interested field and the set of costraints. This behaviour can be extended in many ways but this would lead to higher execution times.

## Additional Notes
<ul>
  <li>A function that exports the new dataset in .csv format is provided</li>
  <li>For each bucket a new tuple is created (this number can be easily changed)</li>
  <li>To test the program we suggest to run it with k=1 and then feed the program with the new dataset to check wether the same paths are taken</li>
  <li>Remember that booleans cannot be anonymized due to behaviour preserving</li>
</ul>
