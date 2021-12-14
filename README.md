# interview-bit--array--spiral-order-matrix-1

-----> Question:

Given a matrix of m * n elements (m rows, n columns), return all elements of the matrix in spiral order.

Example:

Given the following matrix:

[
    [ 1, 2, 3 ],
    [ 4, 5, 6 ],
    [ 7, 8, 9 ]
]
You should return

[1, 2, 3, 6, 9, 8, 7, 4, 5]


-------> Code:

vector<int> Solution::spiralOrder(const vector<vector<int> > &A) {

    int t=0,b=A.size()-1,l=0,r=A[0].size()-1,dir=0;
    vector<int> v;

    while(t<=b && l<=r){
        if(dir==0){
            for(int i=l;i<=r;i++){
                v.push_back(A[t][i]);
            }
            t++;
            dir=1;
        }else if(dir==1){
            for(int i=t;i<=b;i++){
                v.push_back(A[i][r]);
            }
            r--;
            dir=2;
        }else if(dir==2){
            for(int i=r;i>=l;i--){
                v.push_back(A[b][i]);
            }
            b--;
            dir=3;
        }else if(dir==3){
            for(int i=b;i>=t;i--){
                v.push_back(A[i][l]);
            }
            l++;
            dir=0;
        }
    }

    return v;
}
