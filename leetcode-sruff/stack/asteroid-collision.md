# Asteroid Collision



We are given an array `asteroids` of integers representing asteroids in a row.

For each asteroid, the absolute value represents its size, and the sign represents its direction (positive meaning right, negative meaning left). Each asteroid moves at the same speed.

Find out the state of the asteroids after all collisions. If two asteroids meet, the smaller one will explode. If both are the same size, both will explode. Two asteroids moving in the same direction will never meet.

&#x20;

**Example 1:**

```
Input: asteroids = [5,10,-5]
Output: [5,10]
Explanation: The 10 and -5 collide resulting in 10. The 5 and 10 never collide.
```

**Example 2:**

```
Input: asteroids = [8,-8]
Output: []
Explanation: The 8 and -8 collide exploding each other.
```

**Example 3:**

```
Input: asteroids = [10,2,-5]
Output: [10]
Explanation: The 2 and -5 collide resulting in -5. The 10 and -5 collide resulting in 10.
```

**Example 4:**

```
Input: asteroids = [-2,-1,1,2]
Output: [-2,-1,1,2]
Explanation: The -2 and -1 are moving left, while the 1 and 2 are moving right. Asteroids moving the same direction never meet, so no asteroids will meet each other.
```

&#x20;

**Constraints:**

* `2 <= asteroids.length <= 104`
* `-1000 <= asteroids[i] <= 1000`
* `asteroids[i] != 0`

## Solution

```python
class Solution:
    def asteroidCollision(self, asteroids: List[int]) -> List[int]:
        ans =[]
        for asteroid in asteroids:
            while ans and asteroid < 0 and ans[-1] >0:
                if -asteroid > ans[-1]:
                    ans.pop()
                    continue
                elif -asteroid == ans[-1]:
                    ans.pop()
                    break
                else:
                    break
            else:
                ans.append(asteroid)  
        return ans
        
        
        '''
        #brute force
        n = len(asteroids)
        i = 1
        index =1
        while n>i:
            #asteroid only collide when previous one go left and cur one go right
            #case when index pop to zero
            if index == 0:
                index+=1
                i+=1
                continue
            if asteroids[index] < 0 and asteroids[index-1]>0:
                #if both are same size
                if asteroids[index-1] == abs(asteroids[index]):
                    #print("check")
                    asteroids.pop(index)
                    asteroids.pop(index-1)
                    i+=1
                    index-=1
                elif asteroids[index-1] > abs(asteroids[index]):
                    #print(f"check1,{index}")
                    asteroids.pop(index)
                    i+=1
                    #index +=1
                else:
                    #print(f"check2,{i},{index}")
                    asteroids.pop(index-1)
                    index-=1
            else:
                i+=1
                index+=1
                    
        return asteroids
        '''
```
