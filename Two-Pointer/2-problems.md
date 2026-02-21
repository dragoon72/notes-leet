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

# 167.[Two Sum II](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)
here we see that the input array is sorted. now we have to find the index for two numbers which is equal to the target. you think abt the brute
force method first. alright, first step is clear ...now you have thought that the time complexity turns out to be O(n2). it should click your mind that this can
be the case for two pointers and also there are two numbers ffor which we are operating.

okay so now this is an example where we will emply the pointers in front and at the end. so since the array is sorted index 1 and the last will bear some 
int value, check if its greater than the target and if it is then reduce the pointer index and if its lesser then increase the left pointer index keep doimg 
it untill left is still less than right

# 977. [Squares of a sorted array](https://leetcode.com/problems/squares-of-a-sorted-array/description/?envType=problem-list-v2&envId=two-pointers)

so here we ccan see its a sorted array and we need to return an array of the sqaure of the elements of the given array. so my first thought was okay this is $O(n^2)$ ,okay so its two pointers . now what we can do is...one pointer at the start other at the other end and then while traversing the whole array we can check if the absolute value of the start pointer is greater than the pointer at the end and then we can update the square in another array

# 26. [Remove duplicates](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/?envType=problem-list-v2&envId=two-pointers)

