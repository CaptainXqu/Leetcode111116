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
        
        

#.289. Game of Life

1.Live Rules
    
                if(board[i][j]==1){//live cell
                    if(liveRules(board,i,j)<2 || liveRules(board,i,j)>3){//turn to dead(1->0)
                        board[i][j] = -1;
                    }
                }else if(board[i][j]==0){//dead cell
                    if(liveRules(board,i,j) == 3){//turn to alive(0->1)
                        board[i][j] = 2;
                    }
                }
2.Reverse the array

        for(int i=0; i<m;i++){//Reverse
            for(int j=0; j<n; j++){
                if(board[i][j]==-1)
                    board[i][j]=0;
                else if(board[i][j]==2)
                    board[i][j]=1;
            }//end for 
        }//end for
        
3.Find total numbers of "1" from neighbor(Have to take out central point)
        
        for(int x=i-1;x<=i+1;x++){
            for(int y=j-1;y<=j+1;y++){
                if(x>=0 && x<m && y>=0 && y<n){//out of boundary
                    if(Math.abs(board[x][y]) == 1)
                        count++;
                }
            }//end for
        }//end for
        if(board[i][j]==1)//Take out the central point
        	return count-1;
        return count;
        
4.Required update the array at the same time, therefore actually there are four status:

    0->0
    0->1(Need to mark)
    1->0(Need to mark)
    1->1
        
        
#.283. Move Zeroes (Keep the others numbers in right order)

          for(int j=0; j<count;j++){//count = total numbers of zero.
            for(int i=0; i<length;i++){
            }
          }
          
#.268. Missing Number    
  1.Sorted first,then compare each number with index
  
            if(nums[i]!=i){
                order = false;
                miss = i;
                break;
            }
            else
                order = true;
  2.Find the missing number with calcalating.
  
        for(int i=0;i<=nums.length;i++)
            total+=i;
        for(int i=0;i<nums.length;i++)
            sum+=nums[i];
        return total-sum;



#.238. Product of Array Except Self
1.By using division, '0' must be consider:

    No '0'
    one '0'
    two and more '0'

2.No division:

   (a). By using extra result array to store the product of numbers before nums[i];
   
   (b). By using nums array to store the product of numbers after nums[i](include num[i]);
   
   (c). Get the products of each pairs of result[i] and nums[i+1];


            for(int i=0;i<l;i++){
                if(i == 0)
                    output[i] = 1;
                else
                    output[i] = output[i-1] * nums[i-1];
            }
            for(int i=l-1;i>=0;i--){
                if(i < l-1 && i != 0){
                    nums[i] = nums[i] * nums[i+1];
                    output[i] = output[i] * nums[i+1];
                }else if(i == 0)
                    output[i] = nums[i+1];
            }
            
            

#.229. Majority Element II

1.Sorted(T(n)=O(nlogn))

2.Moore vote algorithm 

(The length greater than n/2 has one number, the length greater than n/3 has at most two number exist.)

        for(int num:nums){
            if(majority1 == num){
                count1++;
            }else if(majority2 == num){
                count2++;
            }else if(count1 == 0){
                majority1 = num;
                count1++;
            }else if(count2 == 0){
                majority2 = num;
                count2++;
            }else{
                count1--;
                count2--;
            }
        } 

To check the length of majority number ,then compare the length with n/3;
           
           
           
           
#.228. Summary Ranges
            
Need to pay attention to the first element, last element and single element;           
            

                    if(i+1<nums.length && nums[i+1] == nums[i]+1){//element which nums[i+1] == nums[i]+1
                        right = nums[i+1];
                        count++;
                    }else if(i+1<nums.length && nums[i+1] != nums[i]+1){//element which nums[i+1] != nums[i]+1
                        count++;
                        if(count == 1){
                            result.add(Integer.toString(nums[i]));
                            count = 0;
                        }else if(count > 1){
                            String temp = left + "->" + right;
                            result.add(temp);
                            count = 0;
                        }
                        left = nums[i+1];
                    }else if(i == nums.length-1){//last element
                        if(nums[i]==nums[i-1]+1){
                            right = nums[i];
                            String temp = left + "->" + right;
                            result.add(temp);
                        }else{
                            result.add(Integer.toString(nums[i]));
                        }                    
                    }



#.4. Median of Two Sorted Arrays    

1.Merger two array.

2.Pay attention on (int)5/(int)2

#.11. Container With Most Water

By using two direction pointer,keep tracking the most height pairs of line.


        while(left < right){
            int area = 0;
            if(height[left] <= height[right]){
                area = height[left] * (right - left);
                left++;
            }else{
                area = height[right] * (right - left);
                right--;
            }
            if(area > maxArea)
                maxArea = area;
        }



            
            
            
            
            
            
            
            
