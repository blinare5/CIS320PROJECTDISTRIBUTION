# CIS320PROJECTDISTRIBUTION
CIS320 PROJECT

Code;
mUSArrests<-read.table("https://vincentarelbundock.github.io/Rdatasets/csv/datasets/USArrests.csv",sep = ",", header = T)
class(USArrests)
summary(USArrests)
summary(USArrests$Murder)
summary(USArrests$Assault)
summary(USArrests$UrbanPop)
summary(USArrests$Rape)
dim(USArrests) #50 0bservations, 4 variables
view(USArrests)
USArrests [1,1]
USArrests [1] #Show murders for all states
USArrests[2] #shows Assaults for all states
USArrests [3] #shows Urbanpop for all states
USArrests [4] #shows Rape for all states
library(ggplot2)
ggplot(USArrests) + geom_bar(aes(x=state.name), fill="gray") + coord_flip() + theme(axis.text.y=element_text(size=rel(0.8)))
ggplot(USArrests, aes(x=USArrests$Murder, y=state.name)) + geom_point()+ ylim(0, 20)
x<- runif(100)
y<-x^2 +0.2*x
ggplot(data.frame(x=x,y=y), aes(x=x,y=y))+geom_line()
USArrests<- subset(USArrests, (USArrests$Murder>0 & USArrests$Murder<100 & USArrests$Assault>0 ))
cor(USArrests$Murder, USArrests$Assault) #This is the correlation between arrests and murder
USArrests<- subset(USArrests, (USArrests$Rape>0 & USArrests$Rape<100 & USArrests$UrbanPop>0 ))
cor(USArrests$Rape, USArrests$UrbanPop) #this is the correlation between rape and urbanpopulation
ggplot(segments(ddata))
ggplot(USArrests)+ geom_histogram(aes(x=Murder), binwidth = 2, fill="gray") #distribution of Murders skewed to the left
ggplot(USArrests)+ geom_histogram(aes(x=Rape), binwidth = 2, fill="gray") #bimodal distribution
ggplot(USArrests)+ geom_histogram(aes(x=Assault), binwidth = 20, fill="gray")#multimodal distribution
ggplot(USArrests)+ geom_histogram(aes(x=UrbanPop), binwidth = 2, fill="gray") #multimodal distribution
library(scales)
ggplot(USArrests)+ geom_density(aes(x=Murder)) 
ggplot(USArrests)+ geom_density(aes(x=Assault))
ggplot(USArrests)+ geom_density(aes(x=Rape))
ggplot(USArrests)+ geom_density(aes(x=UrbanPop))

ggplot(USArrests)+ geom_density(aes(x=Murder))+ scale_x_log10(breaks=c(5, 10, 20))+ annotation_logticks(sides = "bt") #Most of the distribution is set close to avg of 10+ murders
ggplot(USArrests)+ geom_density(aes(x=Assault))+ scale_x_log10(breaks=c(50, 100, 200))+ annotation_logticks(sides = "bt") #most of the distribution is set close to over 200 assaults
ggplot(USArrests)+ geom_density(aes(x=Rape))+ scale_x_log10(breaks=c(15, 25, 35))+ annotation_logticks(sides = "bt") #Most of the distribution is set close to avg of 20 to 25 murders
ggplot(USArrests)+ geom_density(aes(x=UrbanPop))+ scale_x_log10(breaks=c(40, 50, 90))+ annotation_logticks(sides = "bt") # most of the distribution is set close to 80-90 arrests in urbanpopulations
p<-ggplot(USArrests, aes(Murder, Assault)) 
p+geom_point() #relationship between murder and assault
p<-ggplot(USArrests, aes(UrbanPop, Rape))
p+geom_point() #relationship between rape and urbanpopulation
install.packages("knitr")
