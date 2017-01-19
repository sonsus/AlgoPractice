###No 37 Truncatable primes
````
The number 3797 has an interesting property. Being prime itself, it is possible to continuously remove digits from left to right,   
and remain prime at each stage: 3797, 797, 97, and 7. Similarly we can work from right to left: 3797, 379, 37, and 3.   
Find the sum of the only eleven primes that are both truncatable from left to right and right to left.    
NOTE: 2, 3, 5, and 7 are not considered to be truncatable primes.
````

####Ans: ver1-exceeded time limit
````python

#truncatable prime
from math import sqrt


def isTruncatable(prime,prime_list):
    str_p=str(prime)
    l=len(str_p)
    if str_p[0]==1 or str_p[-1]==1: return False
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
        elif ob[0]==len(prime_list)-1:
            prime_list.append(cand)
            if isTruncatable(cand,prime_list)==True: 
                res_list.append(cand)
                print(res_list)
    cand+=2


res=0
for nums in res_list:
    res+=nums
print("the answer is %s"%res)
````

####Ans2:
If a number is a composite, there must be a prime number lesser than sqrt("the number")

--> reducing search time
