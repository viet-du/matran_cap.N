# matran_cap.N
import numpy as np
def determinant_laplace(matrix):
    """
    Tính định thức cuar ma trận bằng phương pháp khai triển laplace (đệ quy),
    :param matrix:Ma trận vuông(numpy array hoặc list lông nhau)
    : return:giá trị định thức của ma trận
    """
    matrix = np.array(matrix)
    n = matrix.shape[0]
    #Điều kiện đúng ma trận 1x1
    if n== 1 :
       return matrix[0,0]
    #điệu kiện đúng:ma trận 2x2
    if n == 2:
        return matrix[0 ,0] * matrix[1,1]- matrix[0,1] * matrix[1,0]
    det = 0
    for j in range(n):
        sub_matrix = np.delete(np.delete(matrix, 0 ,axis =0),j, axis =1)#ma trận con
        confactor = (-1) ** j * matrix[0,j] * determinant_laplace(sub_matrix)
        det += confactor
    return det
#nhập ma trận từ người dùng
def input_matrix():
    n = int(input("nhập kích thước ma trận vuông nxn:"))
    matrix = []
    print('nhập từng dòng của ma trận,cách nhau bởi daaus cách:')
    for i in range (n):
       row = list(map(float,input(f"dòng{i+1}:").split()))
       matrix.append(row)
    return np.array(matrix)
#chạy chương trình
matrix = input_matrix()
det = determinant_laplace(matrix)
print('định thức của ma trận là:',det)
