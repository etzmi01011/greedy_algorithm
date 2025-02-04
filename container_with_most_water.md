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

### 解法