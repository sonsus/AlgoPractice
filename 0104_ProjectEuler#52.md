# AlgoPractice
algorithm study started from 2nd.Jan.2017

###0104_ProjectEuler 52 (difficulty: easy)

```python
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
```
[output]
142857 ~0.4s

### charming short! charming fast!
```python
from time import time
start=time()
x=11
while True:
    if (all (number in str(x) for number in str(2*x))):
        if (all (number in str(2*x) for number in str(3*x))):
            if (all (number in str(3*x) for number in str(4*x))):
                if (all (number in str(4*x) for number in str(5*x))):
                    if (all (number in str(5*x) for number in str(6*x))):
                        print(x)
                        break

    x += 1
print(time()-start)
```
[Output]
142857 ~0.3s

### another version
```python
import time
time.clock()
u=11
while True:
    digits=len(str(u))
    if digits ==  len(str(6*u)):
        a = []
        a.append(str(2*u))
        a.append(str(3*u))
        a.append(str(4*u))
        a.append(str(5*u))
        a.append(str(6*u))
        if sorted(str(u)) == sorted(a[0]) == sorted(a[1]) == sorted(a[2]) == sorted(a[3]) == sorted(a[4]):
            print (u,time.clock())
            break
        else: u+=1
    else: u=10**digits+1

```
[Output]
142857 0.33873485952610666
