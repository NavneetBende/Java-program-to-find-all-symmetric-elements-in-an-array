Symmetric Elements in an Array in Java
Here, in this page we will discuss the program to find all symmetric elements in an array in Java programming language. We are given with pairs and need to print those pairs which are symmetric.

Symmetic elements in an array
Explanation :
We are given with an array pairs, inside that array some symmetric pairs exist. The problem statement says that we have to find all symmetric pairs that exist in array. we can simply use two loops and traverse the 2d array.
Example,
Input : arr[5][2] = {{10,20}, {30,40}, {50,60}, {20,10}, {40,30}}
Output : (10,20) (30,40)
Here, we will discuss the following two different methods for printing symmetric pairs in the given set of pairs.

Method 1:  Brute Force
Method 2 : Using Hash-map
Method 1 :
Declare a 2D array for pairs.
Run a outer loop from index  0 to 5
Run an inner loop from index i+1 to 5
Check if(arr[i][0]==arr[j][1] && arr[i][1]==arr[j][0])), then print the arr[i][0] and arr[i][1].
Time and Space Complexity :
Time Complexity : O(n2)
Space Complexity : O(1)
Related Pages
Finding Maximum scalar product of two vectors in an array

Counting the number of even and odd elements in an array

Find maximum product sub-array in a given array

Finding Arrays are disjoint or not

Determine Array is a subset of another array or not

Method 1 : Code in Java
Run
class Main{
    
    public static void main(String arg[])
    {
        int arr[][] = new int[5][2];
        
        arr[0][0] = 1;
        arr[0][1] = 2;
        arr[1][0] = 3;
        arr[1][1] = 4;
        arr[2][0] = 5;
        arr[2][1] = 1;
        arr[3][0] = 4;
        arr[3][1] = 3;
        arr[4][0] = 1;
        arr[4][1] = 5;

        for (int i = 0; i < 5; i++){
            for (int j = i + 1; j < 5; j++){
	            if (arr[i][0] == arr[j][1] && arr[i][1] == arr[j][0])
	                System.out.println("(" + arr[i][0] + ", " + arr[i][1] + ")");
	        }
        }

    }
}
Output :
(3, 4)
(5, 1)
Method 2 :
In this method we will use hash-map,

The first element of pair is used as key and the second element is used as the value.
Traverse all pairs one by one.
For every pair, we check if its second element is in the hash table.
If it is, then compare the first element with the value of the matched entry of the hash table.
If the value and the first element match, then we found symmetric pairs.
Else, insert the first element as a key and second element as value.
Method 2 : Code in Java
Run
import java.util.HashMap;
class Main{
    
    public static void main(String arg[])
    {
        int arr[][] = new int[5][2];
        
        arr[0][0] = 1;
        arr[0][1] = 2;
        arr[1][0] = 3;
        arr[1][1] = 4;
        arr[2][0] = 5;
        arr[2][1] = 1;
        arr[3][0] = 4;
        arr[3][1] = 3;
        arr[4][0] = 1;
        arr[4][1] = 5;

        HashMap<Integer, Integer> hM = new HashMap<Integer, Integer>();
  
        // Traverse through the given array
        for (int i = 0; i < arr.length; i++)
        {
            // First and second elements of current pair
            int first = arr[i][0];
            int sec   = arr[i][1];
             
            // Look for second element of this pair in hash
            Integer val = hM.get(sec);
  
            if (val != null && val == first)
               System.out.println("(" + sec + ", " + first + ")");
                
            else  // Else put sec element of this pair in hash
               hM.put(first, sec);
        }

    }
}
Output :
(3, 4)
(5, 1)
