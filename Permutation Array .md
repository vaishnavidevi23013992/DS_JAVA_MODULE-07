# Ex9 Finding the Longest Length of Nested Set in a Permutation Array
## DATE:
## AIM:
To write a program that finds the length of the longest set s[k] defined as s[k] = { nums[k], nums[nums[k]], nums[nums[nums[k]]], … },where the iteration stops before a duplicate element occurs.

The task is to return the maximum size among all such sets.
## Algorithm

1. Create an array nums[] and a visited[] array to track which elements have been used.
2. For each index k in the array, start forming the set s[k] by repeatedly jumping to nums[k].
3. Continue the jumps until you reach an element already marked as visited, meaning a duplicate would occur.
4. Count the number of unique jumps made in this chain and update the maximum length found so far.
5. After checking all k, return the largest size among all sets s[k].
  

## Program:
```
Program to find the Longest Length of Nested Set in a Permutation Array
Developed by: VAISHNAVIDEVI V
RegisterNumber:  212223040230
```
```
public class LongestSet {

    // Method to find the longest set length
    public static int arrayNesting(int[] nums) {
        int n = nums.length;
        boolean[] visited = new boolean[n];
        int maxLength = 0;

        for (int i = 0; i < n; i++) {
            if (!visited[i]) {
                int count = 0;
                int current = i;

                while (!visited[current]) {
                    visited[current] = true;
                    current = nums[current];
                    count++;
                }

                if (count > maxLength) {
                    maxLength = count;
                }
            }
        }

        return maxLength;
    }

    public static void main(String[] args) {
        int[] nums = {5, 4, 0, 3, 1, 6, 2};

        int result = arrayNesting(nums);
        System.out.println("Longest Set Length: " + result);
    }
}


```

## Output:

<img width="1919" height="613" alt="image" src="https://github.com/user-attachments/assets/af2f4b31-eeb6-4e88-a9c5-21664bdbedd8" />


## Result:
The program successfully computes the longest length of the nested set s[k] for the given permutation array.
