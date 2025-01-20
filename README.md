# Leetcode-2661

# C++

class Solution {
public:
    int firstCompleteIndex(vector<int>& arr, vector<vector<int>>& mat) {
        map<int,pair<int,int>>mp;
        int m=mat.size(),n=mat[0].size();
        for(int i=0;i<m;i++)
        {
            for(int j=0;j<n;j++)
            {
                mp[mat[i][j]]={i,j};
            }
        }
        map<int,int>row,col;
        for(int i=0;i<arr.size();i++)
        {
            row[mp[arr[i]].first]++;
            if(row[mp[arr[i]].first]==n)return i;
            col[mp[arr[i]].second]++;
            if(col[mp[arr[i]].second]==m)return i;
        }
        return 0;
    }
};

# python

class Solution:
    def firstCompleteIndex(self, arr, mat):
        mp = {}
        m, n = len(mat), len(mat[0])
        
        # Map each matrix element to its (row, column) coordinates
        for i in range(m):
            for j in range(n):
                mp[mat[i][j]] = (i, j)
        
        row = {}
        col = {}
        
        # Iterate through the array to find the first complete row or column
        for i in range(len(arr)):
            r, c = mp[arr[i]]
            row[r] = row.get(r, 0) + 1
            if row[r] == n:
                return i
            col[c] = col.get(c, 0) + 1
            if col[c] == m:
                return i
        
        return 0


# Java


import java.util.HashMap;
import java.util.Map;

class Solution {
    public int firstCompleteIndex(int[] arr, int[][] mat) {
        Map<Integer, int[]> mp = new HashMap<>();
        int m = mat.length, n = mat[0].length;
        
        // Map each matrix element to its (row, column) coordinates
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                mp.put(mat[i][j], new int[]{i, j});
            }
        }
        
        int[] row = new int[m];
        int[] col = new int[n];
        
        // Iterate through the array to find the first complete row or column
        for (int i = 0; i < arr.length; i++) {
            int r = mp.get(arr[i])[0];
            int c = mp.get(arr[i])[1];
            
            row[r]++;
            if (row[r] == n) return i;
            
            col[c]++;
            if (col[c] == m) return i;
        }
        
        return 0;
    }
}
