# DataStructureChallenges

# Week 1 Challenge
# 1. FIND THE NUMBER OF PATHS
## The problem is to count all the possible paths from the top left element to the bottom right element of an MxN matrix with the constraint of going ONLY right or down fom each cell. You will have to create the matrix on your own

## Implement a method numPaths(m,n) which take M and N, M meaning number of rows and N meaning number of columns and return the number of paths. Check for the constraint in your function- 1 ≤ M,N ≤ 10 and return -1 for incorrect arguments.



## To solve the problem follow the below idea:
## We can recursively move to right and down from the start until we reach the destination and then add up all valid paths to get the answer.
## Follow the below steps to solve the problem:

## Create a recursive function with parameters as row and column index
## Call this recursive function for N-1 and M-1
## In the recursive function
## If N == 1 or M == 1 then return 1
## else call the recursive function with (N-1, M) and (N, M-1) and return the sum of this
## Print the answer

// A Java program to count all possible paths
// from top left to bottom right

class GFG {

	// Returns count of possible paths to reach
	// cell at row number m and column number n
	// from the topmost leftmost cell (cell at 1, 1)
	static int numberOfPaths(int m, int n)
	{
		// If either given row number is first or
		// given column number is first
		if (m == 1 || n == 1)
			return 1;

		// If diagonal movements are allowed then
		// the last addition is required.
		return numberOfPaths(m - 1, n)
			+ numberOfPaths(m, n - 1);
		// + numberOfPaths(m-1, n-1);
	}

	// Driver code
	public static void main(String args[])
	{
		System.out.println(numberOfPaths(3, 3));
	}
}

// This code is contributed by Sumit Ghosh


Output
6

Time Complexity: O(N * M)
Auxiliary Space: (N * M)

## Normal way
## Count all possible paths from the top left to the bottom right of a M X N matrix using DP:


## Follow the below steps to solve the problem:

## Declare a 2-D array count of size M * N
## Set value of count[i][0] equal to 1 for 0 <= i < M as the answer of subproblem with a single column is equal to 1
## Set value of count[0][j] equal to 1 for 0 <= j < N as the answer of subproblem with a single row is equal to 1
## Create a nested for loop for 0 <= i < M and 0 <= j < N and assign count[i][j] equal to count[i-1][j] + count[i][j-1]
## Print value of count[M-1][N-1]



// A Java program to count all possible paths
// from top left to bottom right

import java.io.*;

class GFG {
    
	// Returns count of possible paths to reach
	// cell at row number m and column number n from
	// the topmost leftmost cell (cell at 1, 1)
	static int numberOfPaths(int m, int n)
	{
		// Create a 2D table to store results
		// of subproblems
		int count[][] = new int[m][n];

		// Count of paths to reach any cell in
		// first column is 1
		for (int i = 0; i < m; i++)
			count[i][0] = 1;

		// Count of paths to reach any cell in
		// first row is 1
		for (int j = 0; j < n; j++)
			count[0][j] = 1;

		// Calculate count of paths for other
		// cells in bottom-up manner using
		// the recursive solution
		for (int i = 1; i < m; i++) {
			for (int j = 1; j < n; j++)

				// By uncommenting the last part the
				// code calculates the total possible paths
				// if the diagonal Movements are allowed
				count[i][j]
					= count[i - 1][j]
					+ count[i]
							[j - 1]; //+ count[i-1][j-1];
		}
		return count[m - 1][n - 1];
	}

	// Driver code
	public static void main(String args[])
	{
		System.out.println(numberOfPaths(3, 3));
	}
}

// This code is contributed by Sumit Ghosh

Output
6
Time Complexity: O(M * N) – Due to nested for loops. 
Auxiliary Space: O(M * N) – We have used a 2D array of size M x N

