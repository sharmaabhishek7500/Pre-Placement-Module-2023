class Solution {
public:
    vector<int> partitionLabels(string S) {
        int n=S.length();
        unordered_map<char,int>mp;
        for (int i=0;i<n;i++)
            mp[S[i]]=i;
        vector<int>res;
        int st=0,end=0;
        for (int i=0;i<n;i++) {
            end=max(end,mp[S[i]]);
            if(end==i){
                res.push_back(end-st+1);
                st=end+1;
            }
        } 
        return res;
    }
};