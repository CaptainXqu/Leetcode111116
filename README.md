# Leetcode111116


# Array
This branch is about Array operation.

#.448. Find All Numbers Disappeared in an Array.
(No extra space and T(n)=O(n))

1. Swap each pair of numbers, and make the array in right order, then compare the elements with index.(Used)
2. Mark each number with -1, the index in the new array which is positive are the answers.()

    	for(int i= 0; i<nums.length; i++){//n
    	    while(nums[i] != i+1 && nums[i] != nums[nums[i]-1]){
    	        int temp = nums[i];
    	        nums[i] = nums[temp-1];
    	        nums[temp-1] = temp;
    	    }
    	}
      //while condition: Make sure the number in right position and two equal numbers would not have been swapped. 
      

    十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十

#.442. Find All Duplicates in an Array.
(No extra space and T(n)=O(n))

1. Sorted the array first, then find the duplicated numbers.(Used)O(nlog(n)
2. Mark each number with -1.

        for(int i= 0;i<nums.length;i++){
            int temp = Math.abs(nums[i]);
            if(nums[temp-1] < 0)
                res.add(temp);
            else
                nums[temp-1] = -1 * nums[temp-1];
        }
    
    十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十
    
#.414. Third Maximum Number T(n)=O(n)

1. Sorted the array first, then use a different array catch the third max number.
        
        for(int i = nums.length-1;i>=0;i--){
                if(i==nums.length-1){
                     interval[2]=nums[i];
                     count = 1;
                }else if(nums[i] != nums[i+1] && count == 1){
                    interval[1]=nums[i];
                    count = 2;
                }else if(nums[i] != nums[i+1] && count == 2){
                    interval[0]=nums[i];
                    count = 0;
                }
            }
2. Sorted the array first, then use a hashset catch the third max number.
            
            Set<Integer> set = new HashSet<Integer>();
            for(int i=nums.length-1;i>=0;i--){
                if(!set.contains(nums[i])){
                    set.add(nums[i]);
                    count++;
                }
                if(count == 1)
                    first = nums[i];
                if(count == 3)
                    return nums[i];
            }
        
        
    十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十
