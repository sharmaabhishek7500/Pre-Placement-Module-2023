class Solution {
public:
    bool f(vector<vector<char>>& board, string &word,int i,int j,int k)
    {
        if(i>=board.size()||i<0||j>=board[0].size()||j<0||board[i][j]!=word[k])
            return false;
        if(k==word.size()-1)
            return true;
        board[i][j]='&';
        string c=to_string(board[i][j]);
        bool ans=f(board,word,i+1,j,k+1)||f(board,word,i,j+1,k+1)||f(board,word,i-1,j,k+1)||f(board,word,i,j-1,k+1);
        board[i][j]=word[k];
        return ans;
    }
    bool exist(vector<vector<char>>& board, string word) {

        for(int i=0;i<board.size();i++)
            for(int j=0;j<board[i].size();j++)
                if(f(board,word,i,j,0))
                    return true;
        return false;
    }
};