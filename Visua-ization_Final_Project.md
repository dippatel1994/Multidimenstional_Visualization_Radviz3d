---
Title: RadViz-3d visualiation of 12 datasets
editor_options:
  chunk_output_type: console
output: 
  html_document: 
    toc: yes
    fig_caption: yes
    keep_md: yes
---
# Task: Plot RadViz 3d and visualize 12 datasets

```r
library(radviz3d)
```

```
## Loading required package: rgl
```

## 1. IRIS dataset

```r
data("iris")
#head(iris)
class(iris$Species)
radialvis3d(data = iris[, -5], cl = factor(iris$Species), domrp = F, doGtrans = F, 
            lwd = 2, alpha = 0.05, pradius = 0.025, class.labels = levels(iris$Species))
```

```
## Warning in rgl.texts(x = structure(c(0.666839560914018, 0.666839560914018, :
## "bitmap" family only supports font 1
```

## 2. Wine dataset

```r
wine <- read.csv(url("http://archive.ics.uci.edu/ml/machine-learning-databases/wine/wine.data"),  header = TRUE)
names(wine) <- c("Alcohol", "Malic acid", "Ash", "Alcalinity of ash", "Magnesium", "Total phenols", "Flavanoids", "Nonflavanoid phenols", "Proanthocyanins", "Color intensity", "Hue", "OD280/OD315 of diluted wines", "Proline", "Last")
class(wine$Alcohol)
#head(wine)
radialvis3d(data = wine[, 2:14], cl = factor(wine$Alcohol), domrp = F, npc = 3,doGtrans = F, 
            lwd = 0, alpha = 0.40, pradius = 0.025, class.labels = unique(wine$Alcohol),
            coord.cex=0.8)
```

```
## Warning in rgl.texts(x = structure(c(-0.327561943915561, 0.0645211973767441, :
## "bitmap" family only supports font 1
```

## 3. Adult dataset

```r
adult <- read.csv(url("http://archive.ics.uci.edu/ml/machine-learning-databases/adult/adult.data"),  header = TRUE)
names(adult) <- c("age", "workclass", "fnlwgt", "education", "education-num", "marital_status", "occupation", "relationship", "race", "sex", "capital_gain", "capital_loss", "hours_per_week", "native_country","salary")

adult$workclass <- as.numeric(factor(adult$workclass))
adult$education <- as.numeric(factor(adult$education))
adult$marital_status <- as.numeric(factor(adult$marital_status))
adult$occupation <- as.numeric(factor(adult$occupation))
adult$relationship <- as.numeric(factor(adult$relationship))
adult$race <- as.numeric(factor(adult$race))
adult$sex <- as.numeric(factor(adult$sex))
adult$native_country <- as.numeric(factor(adult$native_country))
adult$salary <- as.numeric(factor(adult$salary))

#head(adult)
radialvis3d(data = adult[,1:14], cl = factor(adult$salary), domrp = F, doGtrans = F, 
          lwd = 0, alpha = 0.40, pradius = 0.025, class.labels = levels(adult$salary))   
```

```
## Warning in rgl.texts(x = structure(c(-0.316097189286049, 0.0624631413030517, :
## "bitmap" family only supports font 1
```

```
## Warning in rgl.texts(x = structure(c(-0.719360070843596, 0.348382119011348, : No
## text to plot
```

## 4. Abalone dataset

```r
abalone <- read.csv(url("http://archive.ics.uci.edu/ml/machine-learning-databases/abalone/abalone.data"),  header = TRUE)
names(abalone) <- c( "Sex", "Length", "Diameter", "Height", "Whole weight", "Shucked weight", "Viscera weight", "Shell weight ", "Rings")
abalone$Sex <- as.numeric(factor(abalone$Sex))
#head(abalone)
radialvis3d(data = abalone[, 2:8], cl = factor(abalone$Sex), domrp = F, npc = 3,doGtrans = T,
            lwd = 0, alpha = 0.40, pradius = 0.025, class.labels = levels(factor(abalone$Sex)),coord.cex=0.8)
```

```
## Warning in rgl.texts(x = structure(c(-0.438672514309052, 0.0828667211716694, :
## "bitmap" family only supports font 1
```

## 5. Forest Fire dataset

```r
fire <- read.csv("http://archive.ics.uci.edu/ml/machine-learning-databases/forest-fires/forestfires.csv",  header = TRUE)
#head(fire)
fire$month <- as.numeric(factor(fire$month))
fire$day <- as.numeric(factor(fire$day))
#head(fire)
#unique(fire$area)
radialvis3d(data = fire[,1:12], domrp = F, npc = 3,doGtrans = T,
            lwd = 0, alpha = 0.40, pradius = 0.025, class.labels = levels(factor(fire$area)), coord.cex=0.8)
```

```
## Warning in rgl.texts(x = structure(c(0, 0, 0, 0, 0.607219434497599,
## -0.607219434497599, : "bitmap" family only supports font 1
```

## 6. Car evaluation dataset

```r
car <- read.csv(url("http://archive.ics.uci.edu/ml/machine-learning-databases/car/car.data"),  header = TRUE)
names(car) <- c( "buying", "maint", "doors", "persons", "lug_boot", "safety", "result")

car$buying <- as.numeric(factor(car$buying))
car$maint <- as.numeric(factor(car$maint))
car$doors <- as.numeric(factor(car$doors))
car$lug_boot <- as.numeric(factor(car$lug_boot))
car$safety <- as.numeric(factor(car$safety))
#car$result <- as.numeric(factor(car$result))
car$persons <- as.numeric(factor(car$persons))
#head(car)
radialvis3d(data = car[, 1:6], cl= factor(car$result), domrp = T, npc = 6,doGtrans = T,
            lwd = 0, alpha = 0.40, pradius = 0.025, class.labels = levels(factor(car$result)), coord.cex=0.8)
```

## 7. Wine Quality dataset

```r
red_wine <- read.csv(url("http://archive.ics.uci.edu/ml/machine-learning-databases/wine-quality/winequality-red.csv"), sep=";",  header = TRUE)
radialvis3d(data = red_wine[, 1:6], cl = factor(red_wine$quality), domrp = F, npc = 3,doGtrans = F,
            lwd = 0, alpha = 0.40, pradius = 0.025, class.labels = unique(red_wine$quality),
            coord.cex=0.8)
```

```
## Warning in rgl.texts(x = structure(c(1.155, -1.155, 0, 0, 0, 0, 0, 0, 1.155, :
## "bitmap" family only supports font 1
```


```r
white_wine <- read.csv(url("http://archive.ics.uci.edu/ml/machine-learning-databases/wine-quality/winequality-white.csv"), sep=";",  header = TRUE)
radialvis3d(data = white_wine[, 1:6], cl = factor(white_wine$quality), domrp = F, npc = 3,doGtrans = F,
            lwd = 0, alpha = 0.40, pradius = 0.025, class.labels = unique(white_wine$quality),
            coord.cex=0.8)
```

```
## Warning in rgl.texts(x = structure(c(1.155, -1.155, 0, 0, 0, 0, 0, 0, 1.155, :
## "bitmap" family only supports font 1
```

## 8. Heart disease dataset

```r
Heart <- read.csv(url("http://archive.ics.uci.edu/ml/machine-learning-databases/heart-disease/processed.cleveland.data"),  header = TRUE)
names(Heart) <- c( "age", "sex", "cp", "trestbps", "chol", "fbs", "restecg", "thalach", "exang","oldpeak","slope","ca","thal","num")
Heart$ca <- as.numeric(factor(Heart$ca))
Heart$thal <- as.numeric(factor(Heart$thal))
Heart$num <- as.character(factor(Heart$num))
#head(Heart)
radialvis3d(data = Heart[, 1:13], cl = factor(Heart$num), domrp = F, npc = 3,doGtrans = F,
            lwd = 0, alpha = 0.40, pradius = 0.025, class.labels = levels(Heart$num),
            coord.cex=0.8)
```

```
## Warning in rgl.texts(x = structure(c(-0.327561943915561, 0.0645211973767441, :
## "bitmap" family only supports font 1
```

```
## Warning in rgl.texts(x = structure(c(0.889022747579927, -0.214336075420795, : No
## text to plot
```

## 9. Bank dataset

```r
bank <- read.csv("./bank-full.csv", sep=";",  header = TRUE)
#head(bank)
bank$job <- as.numeric(factor(bank$job))
bank$marital <- as.numeric(factor(bank$marital))
bank$education <- as.numeric(factor(bank$education))
bank$default <- as.numeric(factor(bank$default))
bank$housing <- as.numeric(factor(bank$housing))
bank$loan <- as.numeric(factor(bank$loan))
bank$contact <- as.numeric(factor(bank$contact))
bank$month <- as.numeric(factor(bank$month))
bank$poutcome <- as.numeric(factor(bank$poutcome))


radialvis3d(data = bank[, 1:16], cl = factor(bank$y), domrp = F, npc = 3,doGtrans = F,
            lwd = 0, alpha = 0.40, pradius = 0.025, class.labels = levels(bank$y),
            coord.cex=0.8)
```

```
## Warning in rgl.texts(x = structure(c(-0.296365504167263, 0.0588655043004461, :
## "bitmap" family only supports font 1
```

```
## Warning in rgl.texts(x = structure(c(-0.609489309398038, 0.318417245287981, : No
## text to plot
```

## 10. Student Performance dataset

```r
student_mat <- read.csv("./student-mat.csv", sep=",",  header = TRUE)
#head(student_mat)
radialvis3d(data = student_mat[, c(3,7,8,13,14,15,24,25,26,27,28,29,30,31,32)], cl = factor(student_mat$G3), domrp = F, npc = 3,doGtrans = F,
            lwd = 0, alpha = 0.40, pradius = 0.025, class.labels = levels(student_mat$G3),
            coord.cex=0.8)
```

```
## Warning in rgl.texts(x = structure(c(-0.305755675771979, 0.0605860272288542, :
## "bitmap" family only supports font 1
```

```
## Warning in rgl.texts(x = structure(c(-0.847982040439454, 0.35037104884283, : No
## text to plot
```


```r
student_por <- read.csv("./student-por.csv", sep=",",  header = TRUE)
#head(student_por)
#, cl = factor(student_por$G3)
radialvis3d(data = student_por[, c(3,7,8,13,14,15,24,25,26,27,28,29,30,31,32)], domrp = F, npc = 3,doGtrans = T,
            lwd = 0, alpha = 0.40, pradius = 0.025, class.labels = levels(student_por$G3),coord.cex=0.8)
```

```
## Warning in rgl.texts(x = structure(c(-0.305755675771979, 0.0605860272288542, :
## "bitmap" family only supports font 1
```

## 11. Activity monitoring dataset

```r
acivity <- read.csv("./ActivityRecognition-Smatphone.csv",  header = TRUE)
radialvis3d(data = acivity[, 4:83], cl = factor(acivity$ActivityName), domrp = F, npc = 3,doGtrans = F,
            lwd = 0, alpha = 0.40, pradius = 0.025, class.labels = unique(acivity$ActivityName),
            coord.cex=0.8)
```

```
## Warning in rgl.texts(x = structure(c(-0.13423796596555, 0.027393132103219, :
## "bitmap" family only supports font 1
```

## 12. Breast cancer dataset

```r
cancer <- read.csv(url("http://archive.ics.uci.edu/ml/machine-learning-databases/breast-cancer-wisconsin/breast-cancer-wisconsin.data"),  header = TRUE)
names(cancer) <- c( "ID", "radius", "texture", "perimeter", "area", "smoothness", "compactness", "concavity"," concave points","symmetry","fractal_dimension")
cancer$compactness <- as.numeric(factor(cancer$compactness))
#head(cancer)
radialvis3d(data = cancer[, 1:10], cl = factor(cancer$fractal_dimension), domrp = F, npc = 3,doGtrans = F,
            lwd = 0, alpha = 0.30, pradius = 0.025, class.labels = levels(cancer$fractal_dimension),
            coord.cex=0.8)
```

```
## Warning in rgl.texts(x = structure(c(-0.371230446932194, 0.0721117962041017, :
## "bitmap" family only supports font 1
```

```
## Warning in rgl.texts(x = structure(c(-0.331411642365536, -0.00556091776546203, :
## No text to plot
```
