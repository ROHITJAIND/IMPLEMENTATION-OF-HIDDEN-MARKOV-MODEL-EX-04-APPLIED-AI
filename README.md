# EX-04 Implementation of Hidden Markov Model
### Aim: 

<table>
<tr>
<td width=80%>
  
Construct a Python code to find the sequence of hidden states by the known sequence of observances using Hidden Markov Model. Consider two hidden states Sunny and Rainy with observable states,happy and sad.
</td> 
<td>

**DATE :00.00.2024**
</td>
</tr> 
</table>

### Algorithm:
Step 1:Define the transition matrix, which specifies the probability of transitioning from  one hidden state to another.<br>
Step 2:Define the emission matrix, which specifies the probability of observing each possible observation given each hidden state.<br>
Step 3:Define the initial probabilities, which specify the probability of starting in each possible hidden state.<br>
Step 4:Define the observed sequence, which is the sequence of observations need to  be analyzed.<br>
Step 5:Initialize the alpha matrix with zeros, where each row represents a time step and each column represents a possible hidden state.<br>
Step 6:Calculate the first row of the alpha matrix by multiplying the initial  probabilities by the emission probabilities for the first observation.<br>
Step 7:Loop through the rest of the observed sequence and calculate the rest of the alpha matrix by multiplying the emission probabilities by the sum of the product of the previous row of the alpha matrix and the corresponding row of the transition matrix.<br>
Step 8:Calculate the probability of the observed sequence by summing the last row of the alpha matrix.<br>
Step 9:Find the most likely sequence of hidden states by selecting the hidden state with the highest probability at each time step based on the alpha matrix.<br>

### Program:
##### IMPORTING LIBRARY
```Python
import numpy as np
```
##### Define the transition matrix
```Python
transition_matrix =np.array([[0.7,0.3],[0.4,0.6]])
```
##### Define the emission matrix
```Python
emission_matrix =np.array ([[0.1,0.9],[0.8,0.2]])
```
##### Define the initial probabilities
```Python
initial_probabilities = np.array([0.5,0.5])
```
##### Define the observed sequence
```Python
observed_sequence = np.array([1,1,1,0,0,1])
```

##### Initialize the alpha matrix
```Python
alpha = np. zeros ((len(observed_sequence) ,len (initial_probabilities) ) )
```
##### Calculate the first row of the alpha matrix
```Python
alpha [0,:] = initial_probabilities *emission_matrix[:, observed_sequence [0]]
```
##### Loop through the rest of the observed sequence and calculate the rest of the alpha matrix
```Python
for t in range (1, len (observed_sequence) ) :
  for j in range (len (initial_probabilities) ) :
    alpha[t,j]= emission_matrix [j,observed_sequence[t]] *np.sum(alpha[t-1:]*transition_matrix[:, j])
```
<br>
<br>

##### Calculate the probability of the observed sequence
```Python
probability = np.sum(alpha[-1,:])
```
##### Print the probability of the observed sequence
```Python
print ("The probability of the observed sequence is: " ,probability)
```
##### Find the most likely sequence of weather states given the observed sequence
```Python
most_likely_sequence=[]
for t in range (len (observed_sequence)):
    if alpha [t, 0] > alpha [t,1]:
        most_likely_sequence.append ("sunny")
    else:
        most_likely_sequence.append ("rainy")
print("The most likely sequence of Weather States is\n",most_likely_sequence)
```
### Output:
<table border=4>
<tr>
<td>
       
*The probability of the observed sequence is:  0.024066630840582106*
</td>
</tr>
</table>
<br>
<br>
<table border=4>
<tr>
<td>
       
*The most likely sequence of Weather States is<br>
['sunny', 'sunny', 'sunny', 'rainy', 'rainy', 'sunny']*
</td>
</tr>
</table>

### Result:
Thus Hidden Markov Model is implemented using python.

**Developed By: ROHIT JAIN D - 212222230120**

