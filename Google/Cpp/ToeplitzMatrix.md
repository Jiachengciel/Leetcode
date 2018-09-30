描述：“托普利兹矩阵”是指如果从左上角到右下角的同一条主斜线上每个元素都相等的矩阵.

给定一个M x N矩阵，判断是否为“托普利兹矩阵”.

样例
样例 1:

输入: matrix = [[1,2,3,4],[5,1,2,3],[9,5,1,2]]
输出: True
解释:
1234
5123
9512

在上述矩阵中，主斜线上元素分别为 "[9]", "[5, 5]", "[1, 1, 1]", "[2, 2, 2]", "[3, 3]", "[4]", 每一条主斜线上元素都相等，所以返回`True`.


样例 2:

输入: matrix = [[1,2],[2,2]]
输出: False
解释:
主斜线 "[1, 2]" 有不同的元素.
注意事项
matrix 是一个二维整数数组.
matrix 的行列范围都为 [1, 20].
matrix[i][j] 的整数取值范围为[0, 99].


**代码：**
===
    class Solution {
    public:
    /*
     * @param matrix: the given matrix
     * @return: True if and only if the matrix is Toeplitz
     */
        bool isToeplitzMatrix(vector<vector<int>> &matrix) {
            if (matrix.empty())
                return false;
            for(int i=1; i<matrix.size(); i++)           //行数//将每行数组作为一个元素看待，取数组个数
            {
                for(int j=1; j<matrix[0].size(); j++)    //列数// 取第一行元素个数
                {
                    if(matrix[i][j] != matrix[i-1][j-1])
                        return false;
                 }
            }
            return true;
        }
    };
