# container with most water

## 題目

You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `i^th^` line are `(i, 0)` and `(i, height[i])`.
Find two lines that together with the x-axis form a container, such that the container contains the most water.
Return the maximum amount of water a container can store.
Notice that you may not slant the container.


### 程式碼
```c++
#include<iostream>
#include<vector>
#include<algorithm>
using namespace std;

int main(){
    int n;
    vector<int> height;
    int ans=0;
    while(cin>>n){
        height.push_back(n);
    }
    int l=0, r=height.size()-1;
    while(l<r){
        int now=min(height[l], height[r])*(r-l);
        ans=max(ans, now);
        if(height[l]>height[r]){
            r--;
        }
        else{
            l++;
        }
    }
    cout<<ans;
    return 0;
}
```