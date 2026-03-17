## problem  
stock buy or sell 121 
## brute force 
check all pairs (j>i) -> TC will be O(n²)
## edge cases
->single element return 0 
->price always decreasing return 0
##  approach
```class Solution {
    public int maxProfit(int[] prices) {
        int min=prices[0];
        int profit=0;
        for (int i=0;i<prices.length;i++){
            if (prices[i]<min){
                min=prices[i];
            }else{
                profit=Math.max(profit,prices[i]-min);
            }
        }
        return profit;
    }
}```