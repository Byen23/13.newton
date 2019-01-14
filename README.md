# 13.Newton.py
Approximating Square Roots.

# Request - Write a program that computes square roots.

# Analysis - The input to this program is a positive floating point or an integer. The output is a floating-point number representing the square root of the input number. For purposes of comparison, we also output Python's estimate of the square root using math.sqrt. Here is the proposed user interface.

"""  	
	
	Enter a positive number: 3
   	The program's estimate:  1.73205081001
   	Python's estimate:       1.73205080757	
"""

# Design - In the seventeenth century, Sir Isaac Newton discovered an algorithm for approximating the square root of a positive number. Recall that the square root y of a positive number x is the number y such that 2 5 y x. Newton discovered that if one’s initial estimate of y is z, then a better estimate of y can be obtained by taking the average of z together with x / z. The estimate can be transformed by this rule again and again, until a satisfactory estimate is reached.

# A quick session with the Python interpreter shows this method of successive approximations in action. We let x be 25 and our initial estimate, z, be 1. We then use Newton’s method to reset z to a better estimate and examine z to check it for closeness to the actual square root, 5. Here is a transcript of our interaction:

   
'''
	
	
	x = 25
	y = 5			# The actual square root of x
	z = 1			# Our initial approximation
    z - (z + x / z) / 2	# Our First Improvement
	13.0
	
    z = (z + x / z) / 2     # Our second Improvement
	z
	7.0

	z = (z + x / z) / 2     # Our third Improvement -- got it!
	z
	5.0	
''' 

# After three transformations, the value of z is exactly equal to 5, the square root of 25. To include cases of numbers, such as 2 and 10, with irrational square roots, we can use an initial guess of 1.0 to produce floating-point results.

# We now develop an algorithm to automate the process of successive transformations, because there might be many of them, and we don’t want to write them all. Exactly how many of these operations are required depends on how close we want our final approximation to be to the actual square root. This closeness value, called the tolerance, can be compared to the difference between and the value of x and the square of our estimate at any given time. While this difference is greater than the tolerance, the process continues; otherwise, it stops. The tolerance is typically a small value, such as 0.000001.

# Our algorithm allows the user to input the number, uses a loop to apply Newton’s method to compute the square root, and prints this value. Here is the pseudocode, followed by an explanation: 

''' 

	set x to the user's input value 
	set tolerance to 0.000001 
	set estimate to 1.0 
	while True    
		set estimate to (estimate + x / estimate) / 2    
		set difference to abs(x - estimate ** 2)    
		if difference <= tolerance:        
			break 
	output the estimate
'''
            
""" 
	
	Compute the square root of a number. 
	
	1. The input is a number. 
	2. The outputs are the program's estimate of the square root using Newton's method of successives approximations, and	 	       
	   Python's own estimate using math.sqrt. 
"""   
