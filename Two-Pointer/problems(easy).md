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
## code:
    class Solution {
    public:
    void moveZeroes(vector<int>& nums) {
        int slow=0;
        for(int fast=0;fast<nums.size();fast++){
            if(nums[fast]!=0){
                nums[slow++]=nums[fast];
            }
        }
        while(slow<nums.size()){
            nums[slow++]=0;
        }
    }
    };

# 167.[Two Sum II](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)
here we see that the input array is sorted. now we have to find the index for two numbers which is equal to the target. you think abt the brute
force method first. alright, first step is clear ...now you have thought that the time complexity turns out to be O(n2). it should click your mind that this can
be the case for two pointers and also there are two numbers ffor which we are operating.

okay so now this is an example where we will emply the pointers in front and at the end. so since the array is sorted index 1 and the last will bear some 
int value, check if its greater than the target and if it is then reduce the pointer index and if its lesser then increase the left pointer index keep doimg 
it untill left is still less than right

## code:
    class Solution {
    public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int left = 0;
        int right = nums.size() - 1;

        while(left < right) {
            int sum = nums[left] + nums[right];

            if(sum == target)
                return {left + 1, right + 1};  

            else if(sum > target)
                right--;
            else
                left++;
        }

        return {};
    }
    };


# 977. [Squares of a sorted array](https://leetcode.com/problems/squares-of-a-sorted-array/description/?envType=problem-list-v2&envId=two-pointers)

so here we ccan see its a sorted array and we need to return an array of the sqaure of the elements of the given array. so my first thought was okay this is $O(n^2)$ ,okay so its two pointers . now what we can do is...one pointer at the start other at the other end and then while traversing the whole array we can check if the absolute value of the start pointer is greater than the pointer at the end and then we can update the square in another array
## code:
    class Solution {
    public:
    vector<int> sortedSquares(vector<int>& nums) {
        int left=0;
        int right=nums.size()-1;
        while(left<=right){
            if(abs(nums[left])>abs(nums[right])){
                int temp=nums[right];
                nums[right]=nums[left]*nums[left];
                nums[left]=temp;
               
                right--;
            }
        
             else{ 
                nums[right]=nums[right]*nums[right];
                 left++;
            }
        }
        return nums;
    
    }
    };

# 26. [Remove duplicates](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/?envType=problem-list-v2&envId=two-pointers)

Given a sorted array nums, remove the duplicates in-place such that each element appears only once. Return the new length of the array.
You must:  

Modify the input array in place

Use O(1) extra space

Return the length of the unique portion

##### example

Input:  nums = [1, 1, 2]

Output: 2,

nums = [1, 2, ...]

### Idea (Two Pointers)

Because the array is already sorted: All duplicates are adjacent. We can keep two pointers:

i – slow pointer for unique position

j – fast pointer scanning ahead

When nums[j] != nums[i], we found a new unique value!
## code:
    class Solution {
    public:
    int removeDuplicates(vector<int>& nums) {
        int k=0;
        for(int i=0;i<nums.size();i++){
            if(nums[i]!=nums[k]){
                k++;
                nums[k]=nums[i];
            }
        }
        return k+1;
    }
    };


# 541.[Reverse String II](https://leetcode.com/problems/reverse-string-ii/description/?envType=problem-list-v2&envId=w7qep7rj)

So here the question asks ask us to take the 2k parts of the string and then we need to reverse the first k part and leave the other part as it is.
then move on and check for the other 2k pair, if the string ends before getting a 2k pair we reverse the whole left out string.

so our intution should be like this:
<br>
#### Loop Increment:
We use i += 2 * k because the problem asks us to process the string in blocks of $2k$. We only care about the first half of each block.
<br>
#### Reversal Range: reverse function takes two iterators: the beginning of the range and the end (exclusive).The start of our reversal is always s.begin() + i.The end of our reversal is s.begin() + i + k. However, if i + k exceeds the string length (when fewer than $k$ characters remain), we must use s.end() (which is s.begin() + n).

#### Complexity:Time Complexity: $O(n)$, where $n$ is the length of the string. Each character is visited at most twice.

#### Space Complexity: $O(1)$ if we modify the input string in place

## code:
    class Solution {
    public:
    string reverseStr(string s, int k) {
        int n=s.length();

        for(int i=0;i<n;i+=2*k){
            reverse(s.begin()+i,s.begin()+min(i+k,n));
        }
        return s;
    }
    };

# 349.[Intersection of two arrays](https://leetcode.com/problems/intersection-of-two-arrays/description/?envType=problem-list-v2&envId=w7qep7rj)

so, in this question we are supposed to find the intersection of two functions(arrays) and return them with a new array. space complexity O(n).

### Intution:
since there are two arrays what we can do is think of two pointers . we have to think of iterating through the two arrays with two pointers and check for unique numbers. so what we will do is, we know that two pointer works on sorted array, so we sort both the arrays and then iterate and then if our new array is empty or the last element is not the current element in array 1 then we push this element to the back of new array.

## code:
    
    class Solution {
    public:
    vector<int> intersection(std::vector<int>& nums1, std::vector<int>& nums2) {
    sort(nums1.begin(), nums1.end());
    sort(nums2.begin(), nums2.end());

        vector<int> result;
        int i = 0, j = 0;

       
        while (i < nums1.size() && j < nums2.size()) {
            if (nums1[i] == nums2[j]) {
           
                if (result.empty() || result.back() != nums1[i]) {
                    result.push_back(nums1[i]);
                }
                i++;
                j++;
            } else if (nums1[i] < nums2[j]) {
                i++;
            } else {
            
                j++;
            }
        }
        return result;
    }
    };
