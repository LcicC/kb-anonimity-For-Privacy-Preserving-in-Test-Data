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

In order to use a different dataset, the user has to change different values. For the sake of simplicity we grouped all the elements to be 
changed inside a single file which is already written for the example dataset and that can be use as a guide.
The algorithm works on numerical attributes, we recommend to normalize floating point values to integer ones to aviod roundings. Categorical 
fileds that are saved as strings can be turned into numbers.

For what concerns the program to test, we provide also a simple example function which is again in the file above. As it can be noticed, 
if the user wants to write his own program he needs to label all the conditional branches in the way it is done in the example.

The output dataset is provided in <i>.csv</i> format.

## Input Parameters and User Defined Values

Here you can find a detailed list of the input parameters and the value that the user must change to change dataset/program.
