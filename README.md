class Matriz:
    def __init__(self, matrizinha): # matrizinha(nxm) é uma lista composta por n listas, listas estas sendo vetores linha de tamanho m
        self.l=matrizinha
        self.n= len(matrizinha)
        self.m=len(matrizinha[0])
    
    def prod_esq(self,mtr):
        r=[]
        for k in range(mtr.n):
            h=[] 
            for q in range(self.m):
                coiso=0
                for i in range(self.n):
                    coiso+= mtr.l[k][i]*self.l[i][q]
                h.append(coiso)
            r.append(h)
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
     
    "fazer funções que retornam matrizes inversas as elementares"
    def mtr_troca(self,i,j):
        r=[]
        for k in range(self.n):
            lin=[]
            for q in range(self.n):
                if k==i:
                    if q==j:
                        lin.append(1)
                    else: 
                        lin.append(0)
                if k==j:
                    if q==i:
                        lin.append(1)
                    else: 
                        lin.append(0)
                else:
                    if k==q:
                        lin.appenf(1)
                    else:
                        lin.append(0)
            r.append(lin)
        return Matriz(r)


    def PALU(self):
        U= self.l[:]
        Palu={
            
        }
        Palu['A']=Matriz(self.l)
        """ Para achar P eu utilizarei algo chamado pivotamento parcial, não sei se funciona nem como funciona, mas tenho fé"""
        
        for k in range(self.m):
            big= U[0][k] 
            big_line=0 
            for q in range (self.n):
                if U[q][k]>big:
                    big= U[q][k]
                    big_line=q
            U=Matriz(U).troca_linha(k,big_line).l
            if Palu['P'] is None:
                Palu['P']= U.mtr_troca(k,big_line)
            else:
                 Palu['P']= Palu['P'].prod_esq(mtr_troca(k,big_line))
