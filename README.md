# Series-de-Tiempo
Practica
library(foreign)
sociodemo<-read.dbf("C:\\Users\\SALA-C2\\Downloads\\SDEMT215.dbf")
View(sociodemo)
View(sociodemo$CD_A)
table(sociodemo$CLASE1)

sociodemo$R_DEF1<-as.numeric(as.character(sociodemo$R_DEF))
sociodemo$C_RES1<-as.numeric(as.character(sociodemo$C_RES))
sociodemo$EDA1<-as.numeric(as.character(sociodemo$EDA))
precod<-subset(sociodemo,((R_DEF1==00)&(C_RES1==1||C_RES1==3)&(EDA1>=15&EDA1<=98)),select=c(EDA,SEX,HRSOCUP,CLASE2,CLASE1,CLASE3))

attach(precod)
CLASE2V1<-table(CLASE2)
CLASE2V1
hist(CLASE2, )
hist(CLASE2, main="Grafica 1. Distribucion de la 
     Poblacion de 15 anios o mas, 2015",xlab="Tipo de ocupada",
     ylab="Poblacion (miles)",xlim=c(1,4),ylim=c(0,200000),
    border=T,pch=18,col="lightsalmon1")

#GRAFICOS DE PIE

sd1<-subset(sociodemo,CLASE2v=1,select=c(EDA,SEX,HRSOCUP,CLASE2,CLASE1,CLASE3,EDA5C,IMSSISSSTE))
frec<-table(sd1$IMSSISSSTE)
frec
help(pie)
pie(frec,labels=c("IMMS","ISSSTE","Otra","No Recibe","No Especificado"),main="Institucion de atencion medica",col=c("green","red","blue","yellow","orange"))

frec1<-table(sd1$EDA5C)
barplot(frec1)
barplot(frec1,main="cinco grupos de edad",col=c("green","red","blue","gray","yellow","brown"),names=c("menor a 14","14-24","25-44","45-64","65+","na"),ylim=c(0,150000))
help(memory.size)
memory.size
