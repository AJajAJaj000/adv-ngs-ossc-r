## Advanced NGS
### Dr. Rintu Kutum
#### Theme: R
##### Everything's happening in the env 'adv-ngs-ossc-r'

###### Date: 12th Apr, 2023

``` {r}

hello_world <- function () {print ("Hello World")}

add <- function (x, y) {print (x + y)}

subs <- function (x, y) {print (x - y)}

prod <- function (x, y) {print (x * y)}

divs <- function (x, y) {print (x / y)}

absq <- function (x, y) {print (x^2 + y^2 + 2*x*y)}

est_bmi <- function (weight, height) {h = height/100; h2 = h * h; print (weight/h2)}

C2F <- function (C) {print (f=(9/5)+32)}

F2C <- function (F) {print (c=(5/9)*(F-32)}

```

###### Date: 26th Apr, 2023

``` {r}

# data frame

age <- c(23,21,24,20)
name <- c('A', 'D', 'C', 'E')
course <- c('CS', 'BIO', 'CS', 'BIO')

student_info <- data.frame (Age = age, Name = name, Course = course)

# indexing data frame

student_info [3,1] # returns 24; can use student_info [3, 'Age']

# special functions for vectors

rep (c('CS', 'BIO'), times = 2) # repeat inputs

rep (c('CS', 'BIO'), each = 2) # repeat input - first element TWICE and then the second element TWICE

rep (c('CS', 'BIO'), length.out = 5) # repeat and output of the length N

rep (c('CS', 'BIO'), times = c(2,1)) # repeat inputs; control the duplication number of each element

seq (from = 0, to = 16, by = 0.05) # return values from '0' to '16' with a difference of '0.05'

seq (from = 0, to = 16, length.out = 1000) # return '1000' values

test_vec <- c(0:16)

sample (test_vec, 10)

log2count_limit <- sample (test_vec, 10, replace = TRUE)

ge_list <- list ()

for (i in 1:10) {
    ge_list[[i]] <- sample (log2count_limit, 10, replace = TRUE)
}

ge_df <- do.call ('rbind', ge_list)

tail (ge_df)

```
###### Date: 3rd May, 2023

``` {r}

rm (list = ls()) # Careful with:- rm (list = ls ())

source ('ngs-class.R') # Execute the functions stored in the source file

# create data folder & subfolder

dir.create(path='data/demo', recursive = TRUE, showWarnings = FALSE)

unlink ('data/demo', recursive = TRUE) # delete the folder

save (ge_df, file = 'file-name') # save the variable to a file

rm(list=ls())

load ('file-name') # Load the file without executing the functions in it


# CRAN

install.packages('frbs') # Install the package "frbs" (Fuzzy rule based system) from CRAN
library ('package-name') # Load/call the package

```

###### Exercise - running code from 'frbs' vignette

``` {r}

data("iris", package = "datasets")
irisShuffled <- iris[sample(nrow(iris)), ]
irisShuffled[, 5] <- unclass(irisShuffled[, 5])
range.data.input <- apply(iris[, -ncol(iris)], 2, range)
tra.iris <- irisShuffled[1:140, ]
tst.iris <- irisShuffled[141:nrow(irisShuffled), 1:4]
real.iris <- matrix(irisShuffled[141:nrow(irisShuffled), 5], ncol = 1)

```

###### Date: 11th May, 2023

``` {r}

count_gene = list (A=c(), B=c(), C= c(), D= c())

gen_count_patient = function (N=10){sample (0:16000, 10)}

gen_count_patient ()

set.seed(101)

gene_x = gen_count_patient (10000)

hist (gene_x)
hist (log2 (gene_x))

pdf ('figures/05-raw-count-hist.pdf', width = 5, height = 5)
hist(gene_x)
dev.off()

pdf ('figures/05-log2-count-hist.pdf', width = 5, height = 5)
hist(log2(gene_x))
dev.off()

pdf ('figures/05-both-count-hist.pdf', width = 5, height = 5)
hist (gene_x, main = 'raw count')
hist (log2(gene_x), main = 'log2 count')
dev.off()

pdf ('figures/05-both side by side-count-hist.pdf', width = 5, height = 5)
par(mfrow=c(1,2))
hist (gene_x, main = 'raw count')
hist (log2(gene_x), main = 'log2 count')
dev.off()

```

