# 貪婪演算法 Greedy Algorithm

## 介紹
貪婪演算法是一種演算法，可透過在每一步都做出當下最佳的選擇，並期望最終結果也是最佳的。這種演算法的實現透過永遠選擇及時最佳選擇，不考慮未來的結果。

## 優點
- 簡單性：開發貪婪演算法比其他演算法更加直接與簡易。
- 容易分析：分析貪婪演算法的過程較其他涉及複雜遞迴關係和眾多子問題的演算法容易。

## 缺點
- 正確性：要檢驗貪婪演算法是否正確需要深度的了解且複雜。檢驗正確性比設計工作還要困難。

## 主要特徵
- 簡易：貪婪演算法簡單易用，在每一步做出當前選擇避免複雜的計算。
- 效率：能快速尋找適合的結果。
- 有效：在某些情形下，能產生最佳結果。

## 示例
了解貪婪演算法最好的方式是透過實例演示。

### 題目
[Container with most water](https://leetcode.com/problems/container-with-most-water/description/)
***
You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `i^th^` line are `(i, 0)` and `(i, height[i])`.
Find two lines that together with the x-axis form a container, such that the container contains the most water.
Return the maximum amount of water a container can store.
Notice that you may not slant the container.
***
給予一組長度為`n`的正整數數列`height`記錄高度。`n`條垂直直線分別繪製在圖上，`第i條`直線被繪至於X座標`i`上且長為`height[i]`。選擇兩條直線代表容器的兩邊長並回傳容器所能容納的最大水量。
***
### 解法
宣告兩變數`l`與`r`儲存當前左右邊長分別處於的位置，宣告時設為最左`0`與最右`height.size()-1`。計算該邊長組合所能容納的水量並檢查是否為最大結果。若此時左邊長`height[l]`大於右邊長`height[r]`，則紀錄右邊長的座標向左位移`r--`;反之，則記錄左邊長的座標向右位移`l++`。位移完後計算所能容納的水量並檢查是否為最大水量。重複執行直到左邊長座標大於右邊長座標。

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

## 結論
貪婪演算法提供一種簡單且通常有效的方法來解決複雜的問題，透過一系列的選擇得出最佳結果。從簡單的活動選擇到複雜的數據壓縮演算法皆能看到其身影。貪婪演算法直觀易懂，其效率在需要快速找出解決方案的問題十分好用。但由於貪婪演算法只執行一次，皆都是基於當前情況去計算，可能導致準確性問題，最終結果可能並非最佳解。

## 參考資料
[貪婪演算法學習教材](https://github.com/breezy-codes/Greedy-Algorithm)

[LeetCode解題網站](https://leetcode.com/problemset/)

[貪婪演算法筆記](https://medium.com/%E6%8A%80%E8%A1%93%E7%AD%86%E8%A8%98/%E6%BC%94%E7%AE%97%E6%B3%95%E7%AD%86%E8%A8%98%E7%B3%BB%E5%88%97-greedy-algorithm-%E8%B2%AA%E5%A9%AA%E6%BC%94%E7%AE%97%E6%B3%95-236f509200de)
