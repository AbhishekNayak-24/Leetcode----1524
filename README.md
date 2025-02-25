# Leetcode----1524
 Number of Sub-arrays With Odd Sum 
//code in java 
class Solution {
    public int numOfSubarrays(int[] arr) {
        int MOD = 1_000_000_007;
        int oddCount = 0, evenCount = 1; // evenCount starts at 1 to handle single-element odd cases
        int prefixSum = 0, result = 0;

        for (int num : arr) {
            prefixSum += num;
            
            if (prefixSum % 2 == 0) { // Even prefix sum
                result = (result + oddCount) % MOD;
                evenCount++;
            } else { // Odd prefix sum
                result = (result + evenCount) % MOD;
                oddCount++;
            }
        }

        return result;
    }
}
