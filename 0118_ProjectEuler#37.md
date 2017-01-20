###No 37 Truncatable primes
````
The number 3797 has an interesting property. Being prime itself, it is possible to continuously remove digits from left to right,   
and remain prime at each stage: 3797, 797, 97, and 7. Similarly we can work from right to left: 3797, 379, 37, and 3.   
Find the sum of the only eleven primes that are both truncatable from left to right and right to left.    
NOTE: 2, 3, 5, and 7 are not considered to be truncatable primes.
````


####Ans:
#####If a number is composite, there must be a prime number lesser than sqrt("the number")

Assume that there is a composite number which has two primes a,b that is larger than sqrt(the num)       
a>sqrt(num)and b>sqrt(num)   --->   ab>sqrt(num)**2   <==> ab > num    (X)

Therefore there is at least a prime <= sqrt(num) for any composite number


````python
#truncatable prime
from math import sqrt
from time import clock

start=clock()

def isTruncatable(prime,prime_list):
    str_p=str(prime)
    l=len(str_p)
    if str_p[0]==1 or str_p[-1]==1: return False
    elif '5' in str_p[1:-1]: return False
    else:
        for i in range(l):
            if int(str_p[i:]) not in prime_list: return False
        for j in range(1,l):
            if int(str_p[0:j]) not in prime_list: return False
        return True


prime_list=[2,3,5,7,11]
res_list=[]
cand=13
while True:
    if len(res_list)==11: break
    for ob in enumerate(prime_list):
        p=ob[1]
        if int(cand)%p==0: #int(cand/p)*p==cand:
            break
        elif ob[1]>sqrt(cand):
            prime_list.append(cand)
            if isTruncatable(cand,prime_list)==True: 
                print(cand)
                res_list.append(cand)
            break
                
    cand+=2


res=0
for nums in res_list:
    res+=nums
print("the answer is %s"%res)
print("elapsed time is %s s"%(clock()-start))
````
####[output]
23  
37  
53  
73  
313  
317  
373  
797  
3137  
3797  
739397  
the answer is 748317  
elapsed time is 62.343499822498494 s 

