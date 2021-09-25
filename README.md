#include <iostream>
#include<vector>
using namespace std;

class tnode{
    public:
     int data;
     tnode* root;
     tnode* left; tnode* right;
     tnode(int data){
         this->data=data;
         this->left=NULL; this->right=NULL;
     }
};


void print_preorder(tnode* root){
    if(root==NULL){
        return ;
    }
    cout<<root->data<<" ";
    print_preorder(root->left);
    print_preorder(root->right);
}


void print_inorder(tnode* root){
    if(root==NULL){return ;}
    print_inorder(root->left);
    cout<< root->data<<" ";
    print_inorder(root->right);
}

void print_postorder(tnode* root){
    if(root==NULL){return ;}
    
    print_postorder(root->left);
    print_postorder(root->right);
    cout<<root->data<<" ";
}

int number_of_tnodes(tnode* root){
    if(root==NULL){return 0;}
    int ans=1;
    ans=ans+number_of_tnodes(root->left)+number_of_tnodes(root->right);
    return ans;
}

int main(){
    tnode* root=new tnode(1);
    // cout<<root->data;   //will print 1
    root->left= new tnode(2);
    // cout<<root->left->data; //will print 1
    root->right=new tnode(3);
    
    root->left->left= new tnode(4);
    // cout<<root->left->left->data;   // will print 4
    root->left->right= new tnode(5);

    print_preorder(root);
    cout<<endl<<endl;
    print_inorder(root);
    cout<<endl<<endl;
    print_postorder(root);
    cout<<endl;
    cout<<number_of_tnodes(root);


    return 0;
}
