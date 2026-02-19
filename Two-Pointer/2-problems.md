# 283. [Move Zeroes]( https://leetcode.com/problems/move-zeroes/description/)
here we apply fast and slow pointer approach.

think it like this. lets say if we have to do this in one single loop what can we do. first thing which should strike to us is using
two pointer approach. we can say the slow pointer will place the non zero element and fast pointer will traverse the element looking for
the non zero elements. theres no pretty big deal in thinking this if you already know abt the two pointer approach.

so basic idea in this type of two pointer approach is that we start with the start for both the pointers and after we are done with filling the non zero elements 
we will just fill rest of the spaces with 0

so, slow pointer= for filling
fast pointer= for traversing
Input:
[0, 1, 0, 3, 12]
Steps:
Copy 1 → [1, _, _, _, _]

Copy 3 → [1, 3, _, _, _]

Copy 12 → [1, 3, 12, _, _]

Fill zeros → [1, 3, 12, 0, 0]
