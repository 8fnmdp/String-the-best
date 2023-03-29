给定一个字符串 s ，请你找出其中不含有重复字符的 最长子串 的长度。

 

示例 1:

输入: s = "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
示例 2:

输入: s = "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
示例 3:

输入: s = "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
 

提示：

0 <= s.length <= 5 * 104
s 由英文字母、数字、符号和空格组成
/*第一种方法，采用滑动数组解决*/
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        if(s.size() == 0) return 0;
        unordered_set<char> lookup;
        int maxStr = 0;
        int left = 0;
        for(int i = 0; i < s.size(); i++){
            while (lookup.find(s[i]) != lookup.end()){/*循环直到lookup里面没有重复先添加的元素为止*/
                lookup.erase(s[left]);
                left ++;
            }
            maxStr = max(maxStr,i-left+1);/*计算长度*/
            lookup.insert(s[i]);
            if(maxStr+left>=s.size()){
                break;
    }
        }
        return maxStr;
        
    }
};![image](https://user-images.githubusercontent.com/101862032/228130642-674a56b3-e158-47b4-be75-3606486043d7.png)

/*第二种方法采用双指针解决*/
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        if(s.size()==0)
        return 0;
        vector<bool> ans(256);
        int left=0,right=0,maxsize=0;
       while(left<=s.size()){
        if(ans[s[right]]){
            ans[s[left]]=false;
            left++;
        }else{
            ans[s[right]]=true;
            right++;
        }
        if(maxsize<right-left)
         maxsize=right-left;
    if(maxsize+left>=s.size()||right>=s.size()){
        break;
    }
}
return maxsize;
}
};![image](https://user-images.githubusercontent.com/101862032/228130713-deeeba9e-cd33-4490-a501-1ac34227a74a.png)


