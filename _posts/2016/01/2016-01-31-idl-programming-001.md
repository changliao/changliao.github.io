---
 
title: 'IDL programming: control variables in IDL across routines'
date: '2016-01-31T21:17:00.001-08:00'
author: Chang Liao
tags:
- C++
- IDL
modified_time: '2016-03-25T14:05:16.296-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-1832925186899999707
blogger_orig_url: https://changliao.blogspot.com/2016/01/idl-programming-001.html
---

IDL, unlike C++, has its own approach and principle when handling variables 
across routines. These features are often very different with the variable 
scope within C++. 
I will try to answer several key questions and prove them using simple demos. 
Question 1: Will the value of a variable be changed after it’s passed into a 
function and changed inside? 
Demo: 

;;..................................................................................... 
PRO variable_change 
a=1.0 
b=2.0 
PRINT,'Before the operation, a is ',a 
c=plus(a,b) 
PRINT,'After the operation, a is ',a 
END 
FUNCTION plus,a,b 
a=a+b 
RETURN,a 
END 
And the IDL Console output: 
Before the operation, a is 1.00000 
After the operation, a is 3.00000 

;;..................................................................................... 
Conclusion: 
If the value of a variable has been changed inside a routine, it will remains 
changed outside. Question 2: What if this variable is not even passed into any 
routine, but the routine has a variable which has the same name? 
Demo: 

;;..................................................................................... 
FUNCTION plus, m, n 
a= m+n 
print, a 
RETURN, a 
END 
PRO variable_test 
a = 1 
PRINT,a 
b =2 
c= 3 
d= plus(b,c) 
PRINT,d 
PRINT,a 
END 
a is 1 a is 5 d is 5 a is 1 

;;..................................................................................... 
Conclusion: If it's not passed, it won't change even other routines have the 
same variable name. 
Tips: 
Whenever you have many variables which may be passed to other routines, try 
not to use the same variable name as much as possible. A simple solution is to 
get a copy of the variable before changing it. 
Question 3: Then how to define a global variable?Answer: IDL provides common 
and Defsysv to handle global variables. 
Demo: 

;;..................................................................................... 
PRO demo 
COMMON exponent,m 
m=2.0 
result=QROMO('integration', 1.0, 2.0) 
PRINT,'The integration result is', result 
END 
FUNCTION integration,x 
;To integrate the expression: y=x^m+1 
;However variable m is uncertain. 
COMMON exponent,m 
result=x^m+1 
RETURN, result 
END 
And the IDL Console output: 
The integration result is 3.33333 

;;..................................................................................... 
Discussion: 
By reviewing the IDL Helper, as we could see, the COMMON defines a shared 
block to store the variables. And there are more than one way to refer the 
shared block. In the above demo, you can also simply use: COMMON exponent in 
the integration function without specify the m. 
Besides, if a shared block is defined, it can’t be changed in number and type 
in the other functions. Also, the sequence of all variables could be exactly 
the same as you refer. 
Tips: 
Though the COMMON is a traditional way to share variables, it could also cause 
conflicts if not configured well. 
In the Defsysv case: 
The IDL provides system variable way to store global variables as well. The 
defsysv procedure  could create a new system variable with initial value if 
configured. 
Demo: 

;;..................................................................................... 
PRO demo 
DEFSYSV, '!m', 2.0 
result=QROMO('integration', 1.0, 2.0) 
PRINT,'The integration result is', result 
END 
FUNCTION integration,x 
;To integrate the expression: y=x^m+1 
;However variable m is uncertain. 
result=x^!m+1 
RETURN, result 
END 
The console output as: 
The integration result is 3.33333 

;;..................................................................................... 
So it is the same with the common case. And the only thing I did was ‘DEFSYSV, 
'!m', 2.0  ’. It seems that this approach is somewhat easier than ‘common’ 
way. 
However, once defined , the system variable can not be destroyed until the 
whole procedure ends. 
What if the variable we want to configure is a vector? 
The demo will indicate that the ‘defsysv’ won’t allow it. But ‘common’ could! 
Of course, other approaches like uvalue and sav file could also provide 
similar function. 
Especially the uvalue method is frequently used along with defsysv. 
Hope it can help! 
I will present a specific example to solve a complex nonlinear equation using 
the above method in other posts. 