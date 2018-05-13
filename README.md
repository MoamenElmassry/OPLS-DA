# OPLS-DA
Orthogonal Partial Least Squares-Discriminant Analysis (OPLS-DA)

This is an example showing how to use the R package (ropls) that was developed by [Etienne Thévenot](http://sites.unica.it/metabolomicaclinica/events/scientific-school-2016/lecturers/thevenot-etienne/).

The R package (ropls) includes a lot of functionalities, but here I am describing how to get the predictive model and the variable  importance in  projection  (VIP) scores of metabolites that are responsible for samples separation.

## How to use it

* To install the required package, start R and enter
```
source("https://bioconductor.org/biocLite.R")
biocLite("ropls")
```
* To load the library
```
library(ropls)
```
* Reading in the table that have the samples in the rows and the metabolites in the columns. Make sure the first column has the sample names and the second has the group names.
```
data = read.csv("table.csv", header=T, row.names = 1)
class = data[, 1]
dataMatrix = data[, 2:dim(data)[2]]
```
* Building OPLS-DA model
```
data.oplsda = opls(dataMatrix, class, predI = 1, orthoI = NA)
```
* To extract the VIP scores of all metabolites
```
write.csv(getVipVn(data.oplsda), "VIPscores.csv")
```

## Reference
[ropls](https://bioconductor.org/packages/release/bioc/html/ropls.html)
