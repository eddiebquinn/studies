topic: #Mathematics 
Source: GCP A-Level Mathematics (Edexcel) - Complete Revisions & Practise

---

- In proof by exhaustion you break thing down into two or more cases. You have to make sure that your cases cover all possible situations, then prove separatley that the statement is true for each case

## Example
> **Prove the following statement:** "For any integer $x$, the value of $f(x)=x^3+x+1$ is an odd integer"

Two prove this assertion you spilt it into two cases
1) $x$ is an even number
2) $x$ is an odd number

### Case 1
if $x$ is even, then it can be written as $x=2n$, for some integer $n$ (see [[Mathematical Definitions#Even number|Definition of an even number]]). You then can sub this into the function

$$f(x)=x^3+x+1$$
$$f(2n)=(2n)^3+2n+1$$
$$f(2n)=8n^3+2n+1$$
$$f(2n)=2(4n^3+n)+1$$
If we say that $z=(4n^3+n)$ we can make the following conclusions:
$n$ is an integer $\implies$ $z$ is an integer $\implies$ $2z$ is even $\implies$ $2z+1$ is odd

### Case 2
If $x$ is odd, then it can be written as $x=2m+1$, for some integer $m$ (see [[Mathematical Definitions#Odd number|Definition of an odd number]]). You can then sub this into the original function and simplify
$$f(2m+1)=(2m+1)^3+(2m+1)+1$$
$$f(2m+1)=(8m^3+12m^2+6m+1)+2m+1+1$$
$$f(2m+1)=8m^3+12m^2+8m+3$$
$$f(2m+1)=2(4m^3+6m^2+4m+1)+1$$
If we say that $z=(4m^3+6m^2+4m+1)$ we can make the following conclusions 
$m$ is an integer $\implies$ $z$ is an integer $\implies$ $2z$ is an even intereger $\implies$ $2z+1$ is odd

Given the conclusions drawn in both case 1 and 2, we have proven the original assertion