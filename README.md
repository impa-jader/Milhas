
class Matriz:
    def __init__(self, matrizinha): # matrizinha(nxm) é uma lista composta por n listas, listas estas sendo vetores linha de tamanho m
        self.l=matrizinha
        self.n= len(matrizinha)
        self.m=len(matrizinha[0])
    
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
     
m=Matriz([[1,5,3],[9,4,5],[3,1,7]])
print(m.l)
print(m.troca_linha(0,2).l)
print(m.elementar(1,1,-9,0).l)
