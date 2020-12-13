# Support-Vector-Machine
### Support vector machine

muscle<-read.table("Muscle.txt", header = TRUE, sep = "|", dec = ",")

```
```{r}
library(tidyverse)
library(ggplot2)
qplot(Ankle_stance_even,Ankle_stance_uneven, data = muscle, color=Gender)

library(e1071)
muscle1<-muscle%>% select(Gender, Ankle_stance_even, Ankle_stance_uneven)
Gender1<-as.factor(muscle1$Gender)
philant.mod<-svm(Gender1~Ankle_stance_even+Ankle_stance_uneven, data = muscle,kernel="linear",
cost=10, scale=FALSE)
summary(philant.mod)
plot(philant.mod, data = muscle1)

```

```{r}
muscle2<-muscle%>% select(Gender, Ankle_stance_uneven, Knee_stance_uneven)
Gender1<-as.factor(muscle2$Gender)
philant.mod1<-svm(Gender1~Ankle_stance_uneven+Knee_stance_uneven, data = muscle2,kernel="polynomial",
cost=1, scale=FALSE)
summary(philant.mod1)
plot(philant.mod1, data = muscle2)



muscle2<-muscle%>% select(Gender, Ankle_stance_uneven, Knee_stance_uneven)
Gender1<-as.factor(muscle2$Gender)
philant.mod1<-svm(Gender1~Ankle_stance_uneven+Knee_stance_uneven, data = muscle2,kernel="radial",
cost=5, scale=FALSE)
summary(philant.mod1)
plot(philant.mod1, data = muscle2)


muscle2<-muscle%>% select(Gender, Ankle_stance_uneven, Knee_stance_uneven)
Gender1<-as.factor(muscle2$Gender)
philant.mod1<-svm(Gender1~Ankle_stance_uneven+Knee_stance_uneven, data = muscle2,kernel="sigmoid",
cost=1, scale=FALSE)
summary(philant.mod1)
plot(philant.mod1, data = muscle2)
```
