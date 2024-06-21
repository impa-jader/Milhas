class Matriz:
    def __init__(self, matrizinha): # matrizinha(nxm) é uma lista composta por n listas, listas estas sendo vetores linha de tamanho m
        self.l=matrizinha
        self.n= len(matrizinha)
        self.m=len(matrizinha[0])
    
    def prod_esq(self,mtr):
        r=[[0]*self.m]*mtr.n 
        for k in range(len(r)): 
            for q in range(len(r[k])):
                coiso=0
                for i in range(self.n):
                    coiso+= mtr.l[k][i]*self.l[i][q]
                r[k][q]=coiso
        return Matriz(r)
        
    def troca_linha(self,i: int,j: int):
        r=self.l[:]
        r[i]=self.l[j]
        r[j]=self.l[i]
        return Matriz(r)
    def elementar(self,a_1,i,a_2,j):# L_i<- L_i*a_1+L_j*a_2
        r= self.l[:]
        for k in range(self.m):
            r[i][k]= r[i][k]*a_1 +r[j][k]*a_2
        return Matriz(r)
     
    def PALU(self):
        U= self.l[:]
        Palu={
            
        }
        Palu[A]=Matriz(self.l)
        """ Para achar P eu utilizarei algo chamado pivotamento parcial, não sei se funciona nem como funciona, mas tenho fé"""
        
A= Matriz([[1,2],[3,0]])
B= Matriz([[2,3],[4,5]])
print(A.prod_esq(B).l)
M=Matriz([[1,5,3],[9,4,5],[3,1,7]])
print(M.l)
print(M.troca_linha(0,2).l)
print(M.elementar(1,1,-9,0).l)
