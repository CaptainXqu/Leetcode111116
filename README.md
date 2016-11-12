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

#.289. Game of Life

(A)Live Rules
    
    if(board[i][j]==1){//live cell
                    if(liveRules(board,i,j)<2 || liveRules(board,i,j)>3){//turn to dead(1->0)
                        board[i][j] = -1;
                    }
                }else if(board[i][j]==0){//dead cell
                    if(liveRules(board,i,j) == 3){//turn to alive(0->1)
                        board[i][j] = 2;
                    }
                }
(B)Reverse the array

    for(int i=0; i<m;i++){//Reverse
            for(int j=0; j<n; j++){
                if(board[i][j]==-1)
                    board[i][j]=0;
                else if(board[i][j]==2)
                    board[i][j]=1;
            }//end for 
        }//end for
        
(C)Find total numbers of "1" from neighbor(Have to take out central point)
        
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
        

    十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十十
    
    
