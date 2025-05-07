# EX 3D Pattern Matching
## DATE:
## AIM:
To write a python program to implement pattern matching on the given string using Brute Force algorithm.



## Algorithm
1. Initialize Pointers:

Set two pointers, i = 0 (for the text string s1) and j = 0 (for the pattern string s2).

2. Iterate Through Both Strings:

Use a while loop to iterate over both s1 and s2 as long as both pointers are within the bounds of their respective strings (i < len(s1) and j < len(s2)).

3. Match Characters:

If the characters s1[i] and s2[j] match, increment both pointers (i++ and j++).

If there is a mismatch, reset the pointer i to i - j + 1 (which means sliding the window of comparison forward by the amount that the pattern string s2 has already matched) and reset j = 0 (start again from the beginning of s2).

4. Check for a Complete Match:

If j becomes equal to len(s2), it indicates that all characters of s2 have been matched within s1. In that case, return the starting index i - len(s2) (this is where s2 starts in s1).

5. Return Result:

If the while loop completes without finding a full match, return 0 (indicating no match was found).  

## Program:
```
/*
Program to implement the Pattern Matching.
Developed by: NAGINENI ROHITH
Register Number:  212222040105
*/
```
```
def BF(s1,s2):
    i = 0
    j = 0
    while(i < len(s1) and j < len(s2)):
        if(s1[i] ==  s2[j]):
            i += 1
            j += 1
        else:
            i = i - j + 1
            j = 0
    if(j >= len(s2)):
        return i - len(s2)
    else:
        return 0
  
if __name__ == "__main__":
    a1=input()  #"abcaaaabbbbcccabcbabdbcsbbbbnnn"
    a2=input()  #'ccabcba'
    b=BF(a1,a2)
    print(b)

```

## Output:
![image](https://github.com/user-attachments/assets/6dc95abc-7495-4072-b7f8-191100dfeffd)


## Result:
The brute force substring search program executed successfully and returned the starting index of the match or 0 if no match was found.
