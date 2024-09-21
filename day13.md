# day13 二叉树

二叉树
![](https://code-thinking-1253855093.file.myqcloud.com/pics/20200806191109896.png)
递归法实现的话就只需要记住前中后顺序就行了，当遇到空节点就return

前序
```cpp
class Solution {
public:
// 递归
    // void traversal(TreeNode* root, vector<int> &vec) {
    //     if(root == nullptr){
    //         return;
    //     }
    //     vec.push_back(root->val);
    //     traversal(root->left, vec);
    //     traversal(root->right,vec);
    // }
    // vector<int> preorderTraversal(TreeNode* root) {
    //     vector<int> res;
    //     if(root != nullptr) {
    //         traversal(root, res);
    //     }
    //     return res;
    // }
// 迭代
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> res;
        stack<TreeNode*> st;
        if(root != nullptr) {
            st.push(root);
            while(!st.empty()){
                TreeNode*cur = st.top();
                st.pop();
                res.push_back(cur->val);
                if (cur->right) st.push(cur->right);
                if (cur->left) st.push(cur->left);
            }
        }
        return res;
    }
};```

中序
```cpp
class Solution {
public:
    // void traversal(TreeNode* root, vector<int> &vec) {
    //     if(root == nullptr){
    //         return;
    //     }
    //     traversal(root->left, vec);
    //     vec.push_back(root->val);

    //     traversal(root->right,vec);
    // }
    // vector<int> inorderTraversal(TreeNode* root) {
    //     vector<int> res;
    //     if(root != nullptr) {
    //         traversal(root, res);
    //     }
    //     return res;
    // }
// 迭代法
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> res;
        if(root != nullptr) {
            stack<TreeNode*>st;
            TreeNode* cur = root;
            while(cur != nullptr || !st.empty()){
                if(cur != nullptr) {
                    st.push(cur);
                    cur = cur->left;
                } else{
                    TreeNode* tem = st.top();
                    st.pop();
                    res.push_back(tem->val);
                    cur = tem->right;
                }
            }
        }
        return res;
    }
};
```
后序
```cpp

class Solution {
public:
    // void traversal(TreeNode* root, vector<int> &vec) {
    //     if(root == nullptr){
    //         return;
    //     }
    //     traversal(root->left, vec);
    //     traversal(root->right,vec);
    //     vec.push_back(root->val);

    // }
    // vector<int> postorderTraversal(TreeNode* root) {
    //     vector<int> res;
    //     if(root != nullptr) {
    //         traversal(root, res);
    //     }
    //     return res;
    // }
    // 迭代
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> res;
        stack<TreeNode*> st;
        if(root != nullptr) {
            st.push(root);
            while(!st.empty()){
                TreeNode*cur = st.top();
                st.pop();
                res.push_back(cur->val);
                if (cur->left) st.push(cur->left);
                if (cur->right) st.push(cur->right);

            }
        }
        reverse(res.begin(), res.end());
        return res;
    }
};
```
