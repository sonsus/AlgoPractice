# AlgoPractice
algorithm study started from 2nd.Jan.2017

###0104_ProjectEuler 52 (difficulty: easy)

#!/bin/python3
from time import time

def findsmallest(x):
	while True:
		str1x=sorted(str(x))
		#print("current x is %s"%x)
		num_pow=len(str1x)-1
		if len(str(x*6))>num_pow+1:
			x=10**(num_pow+1)+1
			continue
		else:
			for i in range(2,7):
				strix=sorted(str(i*x))
				if strix!=str1x: 
					x+=1
					break
				elif i==6: return x

if __name__=="__main__":
	start=time()
	x=11
	res=findsmallest(x)
	for i in range(1,7): print(res*i)
	elapsed=time()-start
	print("elapsed time is %s"%elapsed)
