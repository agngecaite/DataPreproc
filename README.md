# DataPreproc
Instaliuojamas paketas "haven".

```
install.packages("haven")
require(haven)
```

Atidaromas ir sutvarkomas duomenų failas.
```
donates <- choose.files()
donate <- read_sas(donates)
cleardon<- donate[complete.cases(donate),]
write.csv(cleardon, "cleardonate.csv", row.names = FALSE)
```
Apskaičiuojami kvartiliai, viršutinis ir apatinis rėžiai, filtruojamas duomenų failas pagal pirmojo ketvirčio duomenis.
```
IQR(cleardon$Qtr1)
quantile(cleardon$Qtr1, probs=c(0.25,0.75))
upper1=quantile(cleardon$Qtr1, probs = 0.75)+3*IQR(cleardon$Qtr1)
lower1=quantile(cleardon$Qtr1, probs = 0.25)-3*IQR(cleardon$Qtr1)
filter(cleardon, cleardon$Qtr1<upper1 & cleardon&Qtr1>lower1)
boxplot(cleardon$Qtr1)
```
Tas pats padaroma ir su kitais trimis duomenų kintamaisiais.
```
quantile(cleardon$Qtr2, probs=c(0.25,0.75))
IQR(cleardon$Qtr2)
upper2=quantile(cleardon$Qtr2, probs = 0.75)+3*IQR(cleardon$Qtr2)
lower2=quantile(cleardon$Qtr2, probs = 0.25)-3*IQR(cleardon$Qtr2)
filter(cleardon, cleardon$Qtr2<upper2 & cleardon&Qtr2>lower2)
boxplot(cleardon$Qtr2)

IQR(cleardon$Qtr3)
quantile(cleardon$Qtr3, probs=c(0.25,0.75))
upper3=quantile(cleardon$Qtr3, probs = 0.75)+3*IQR(cleardon$Qtr3)
lower3=quantile(cleardon$Qtr3, probs = 0.25)-3*IQR(cleardon$Qtr3)
filter(cleardon, cleardon$Qtr3<upper2 & cleardon&Qtr2>lower3)
boxplot(cleardon$Qtr3)

IQR(cleardon$Qtr4)
quantile(cleardon$Qtr4, probs=c(0.25,0.75))
upper4=quantile(cleardon$Qtr4, probs = 0.75)+3*IQR(cleardon$Qtr4)
lower4=quantile(cleardon$Qtr4, probs = 0.25)-3*IQR(cleardon$Qtr4)
filter(cleardon, cleardon$Qtr4<upper4 & cleardon&Qtr4>lower4)
boxplot(cleardon$Qtr4)
```
