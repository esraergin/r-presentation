Introduction to R
========================================================
author: İsmail SEZEN
date: 2016-10-03
width: 1440
height: 1280
font-family: 'Helvetica'

Need Help?
========================================================

- [An introduction to R](http://cran.us.r-project.org/doc/manuals/R-intro.pdf) (Book)
- [Ask to google](google.com) (Best)
- [R-help maling list](https://www.r-project.org/mail.html)
  - [Subscribe](https://stat.ethz.ch/mailman/listinfo/r-help)
  - [How to ask a good question?](https://www.r-project.org/posting-guide.html)
  - Do NOT ask for your homework!

How to get help from R?
```
help.start()
help(lm)
?lm
example(lm)
?help
```

Preliminary
========================================================
R commands;

- are Case Sensitive
- can be separated either by a semi-colon (‘;’), or by a newline.
- Hashmark (‘#’) means _Comment_ (is it required? _absolutely YES_)


```r
# this is a comment
A = 5; a = 10 # R is case sensitive
print(paste("A is", A))
print(paste("a is", a))
cat("A and a are equal? = ", A == a)
cat("My name is", Sys.info()["user"])
```


```
[1] "A is 5"
```

```
[1] "a is 10"
```

```
A and a are equal? =  FALSE
```

```
My name is isezen
```

### SEE ALSO

```r
?print; ?paste; ?cat
```

Data permanency and removing objects
========================================================

The entities that R creates and manipulates are known as _objects_.

**Object:** variables, arrays of numbers, character strings, functions or
more general structures built from such components


```r
ls() # list objects in the current session
```

```
[1] "a" "A"
```

```r
rm(a) # remove object named a
ls() # list again to see what we have
```

```
[1] "A"
```

```r
print(A) # print a to the console
```

```
[1] 5
```

If you indicate that you want to do this, the objects are written to a file
called **.RData** in the current directory, and the command lines used in
the session are saved to a file called **.Rhistory**.


### SEE ALSO

```r
?ls; ?rm
```

Simple Manipulations
========================================================

## Assignment

Use always `->` or `<-` symbol combination if you intend to an assignment


```r
# Assignment
x <- c(10.4, 5.6, 3.1, 6.4, 21.7)
assign("x", c(10.4, 5.6, 3.1, 6.4, 21.7))
c(10.4, 5.6, 3.1, 6.4, 21.7) -> x
y <- c(x, 0, x) # c is abbreviation for combine
print(y)
```

```
 [1] 10.4  5.6  3.1  6.4 21.7  0.0 10.4  5.6  3.1  6.4 21.7
```

```r
1/x
```

```
[1] 0.09615385 0.17857143 0.32258065 0.15625000 0.04608295
```

### SEE ALSO

```r
?c; ?assign
```

Simple Manipulations
========================================================

## Vector arithmetic

The elementary arithmetic operators: **+**, **-**,_*_, **/** and **^**


```r
x ^ 2 # take the square
sqrt(y) # square root
x/y
v <- 2*x + y + 1
length(v) # what is the length of v? why?
```

Shorter vectors in the expression are recycled as often as need be
(perhaps fractionally) until they match the length of the longest vector.

### SEE ALSO

```r
??"arithmetic operations"; ?log; ?exp; ?sin; ?cos; ?tan; ?sqrt
```

Simple Manipulations
========================================================

## Vector arithmetic

anything else? (max, min, sum, mean, var, std)


```r
sum(x) # sum of values in x vector
sum(x)/length(x) # calculate mean
mean(x) # easier mean calculation
min(x); max(x)
```

### SEE ALSO


```r
?var; ?std; ?range; ?sort; ?order; ?mean; ?sum; ?summary; ?abs
```

Simple Manipulations
========================================================

## Generate regular sequences


```r
5:17
```

```
 [1]  5  6  7  8  9 10 11 12 13 14 15 16 17
```


```r
seq(-5, 5, by = 0.2)
seq(length = 51, from = -5, by = 0.2)
```


```
 [1] -5.0 -4.8 -4.6 -4.4 -4.2 -4.0 -3.8 -3.6 -3.4 -3.2 -3.0 -2.8 -2.6 -2.4
[15] -2.2 -2.0 -1.8 -1.6 -1.4 -1.2 -1.0 -0.8 -0.6 -0.4 -0.2  0.0  0.2  0.4
[29]  0.6  0.8  1.0  1.2  1.4  1.6  1.8  2.0  2.2  2.4  2.6  2.8  3.0  3.2
[43]  3.4  3.6  3.8  4.0  4.2  4.4  4.6  4.8  5.0
```

### SEE ALSO


```r
?seq
```

Simple Manipulations
========================================================

## Repeat an object


```r
rep(x, times = 5)
rep(x, each = 5)
```


```
 [1] 10.4  5.6  3.1  6.4 21.7 10.4  5.6  3.1  6.4 21.7 10.4  5.6  3.1  6.4
[15] 21.7 10.4  5.6  3.1  6.4 21.7 10.4  5.6  3.1  6.4 21.7
```

```
 [1] 10.4 10.4 10.4 10.4 10.4  5.6  5.6  5.6  5.6  5.6  3.1  3.1  3.1  3.1
[15]  3.1  6.4  6.4  6.4  6.4  6.4 21.7 21.7 21.7 21.7 21.7
```

### SEE ALSO


```r
?rep
```


Simple Manipulations
========================================================

## Logical Vectors

The elements of a logical vector can have the values TRUE, FALSE, and NA
(for “not available”). Always use **TRUE** and **FALSE**.


```r
5 > 10
x > 13
as.numeric(x > 13)
```


```
[1] FALSE
```

```
[1] FALSE FALSE FALSE FALSE  TRUE
```

```
[1] 0 0 0 0 1
```

### SEE ALSO


```r
?"Comparison"
```

Simple Manipulations
========================================================

## Missing Values

When an element or value is “not available” or a “missing value” in the
statistical sense, a place within a vector may be reserved for it by assigning
it the special value NA.


```r
z <- c(1:3, NA) # a vector contains an NA
is.na(z) # which element(s) of z is NA?
```

```
[1] FALSE FALSE FALSE  TRUE
```

```r
z == NA # wrong way!
```

```
[1] NA NA NA NA
```

```r
0/0 # meaningless
```

```
[1] NaN
```

is.na(xx) is TRUE both for NA and NaN

### SEE ALSO


```r
?is.na; ?is.finite
```

Simple Manipulations
========================================================

## Character vectors

they are denoted by a sequence of characters delimited by the double quote
character


```r
labs <- paste(c("X","Y"), 1:10, sep="")
print(labs)
```

```
 [1] "X1"  "Y2"  "X3"  "Y4"  "X5"  "Y6"  "X7"  "Y8"  "X9"  "Y10"
```


### SEE ALSO


```r
?paste; ?paste0
```

Simple Manipulations
========================================================

## Indexing, selecting and modifying


```r
x[3] <- NA # set 3th element of x to NA
print(x)
```

```
[1] 10.4  5.6   NA  6.4 21.7
```

```r
!is.na(x) # The ones that are not NA
```

```
[1]  TRUE  TRUE FALSE  TRUE  TRUE
```

```r
non_na_x <- x[!is.na(x)] #non-NA values of x
print(non_na_x)
```

```
[1] 10.4  5.6  6.4 21.7
```


### SEE ALSO


```r
?`[[`
```

Simple Manipulations
========================================================

## Indexing, selecting and modifying


```r
# create a random integer array to
# represent month
set.seed(2)
month <- round(runif(30, 1, 12))
(char_month <- month.abb[month]) # get month names
```

```
 [1] "Mar" "Sep" "Jul" "Mar" "Nov" "Nov" "Feb" "Oct" "Jun" "Jul" "Jul"
[12] "Apr" "Sep" "Mar" "May" "Oct" "Dec" "Mar" "Jun" "Feb" "Aug" "May"
[23] "Oct" "Mar" "May" "Jun" "Mar" "May" "Dec" "Feb"
```

```r
which(char_month == "Jun") # Which are June?
```

```
[1]  9 19 26
```

```r
which(month == 6) # same as above
```

```
[1]  9 19 26
```


### SEE ALSO


```r
?set.seed; ?runif; ?round; ?which; ?which.max; ?which.min
```

Simple Manipulations
========================================================

## Indexing, selecting and modifying


```r
(char_month[1:12]) # select first 12 months
```

```
 [1] "Mar" "Sep" "Jul" "Mar" "Nov" "Nov" "Feb" "Oct" "Jun" "Jul" "Jul"
[12] "Apr"
```

```r
(char_month[-(1:20)]) # exclude first 20
```

```
 [1] "Aug" "May" "Oct" "Mar" "May" "Jun" "Mar" "May" "Dec" "Feb"
```

```r
# exclude June from vector
(char_month[-which(month == 6)])
```

```
 [1] "Mar" "Sep" "Jul" "Mar" "Nov" "Nov" "Feb" "Oct" "Jul" "Jul" "Apr"
[12] "Sep" "Mar" "May" "Oct" "Dec" "Mar" "Feb" "Aug" "May" "Oct" "Mar"
[23] "May" "Mar" "May" "Dec" "Feb"
```


Simple Manipulations
========================================================

## Indexing, selecting and modifying


```r
# use months and month names together
# set names of month
names(month) <- char_month
print(month)
```

```
Mar Sep Jul Mar Nov Nov Feb Oct Jun Jul Jul Apr Sep Mar May Oct Dec Mar 
  3   9   7   3  11  11   2  10   6   7   7   4   9   3   5  10  12   3 
Jun Feb Aug May Oct Mar May Jun Mar May Dec Feb 
  6   2   8   5  10   3   5   6   3   5  12   2 
```

```r
(month[(month == 6)])
```

```
Jun Jun Jun 
  6   6   6 
```


### SEE ALSO


```r
?names; ?colnames; ?rownames
```

Simple Manipulations
========================================================

## Other types of objects

- Matrices
- factors
- lists
- Data frames (same as matrix but columns can be of different types)


```r
# also try byrow = TRUE.
(m <- matrix(1:20, nrow = 5, ncol = 4))
```

```
     [,1] [,2] [,3] [,4]
[1,]    1    6   11   16
[2,]    2    7   12   17
[3,]    3    8   13   18
[4,]    4    9   14   19
[5,]    5   10   15   20
```


### SEE ALSO


```r
?matrix; ?factor; ?list; ?data.frame
```

Objects
========================================================

## Everything is an _object_ in R.

- Atomic objects are all of the same type. (numeric, complex, logical, character ...)


```r
(z <- 0:9)
```

```
 [1] 0 1 2 3 4 5 6 7 8 9
```

```r
(digits <- as.character(z))
```

```
 [1] "0" "1" "2" "3" "4" "5" "6" "7" "8" "9"
```

### SEE ALSO


```r
?as.numeric; ?as.character; ?as.logical; ?as.matrix
```


Objects
========================================================

## Everything is an _object_ in R.

- Other high level objects (matrix, data.frame, list ...)


```r
digit <- 0:9
name <- c("zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine")
df <- data.frame(digit, name)
head(df)
```

```
  digit  name
1     0  zero
2     1   one
3     2   two
4     3 three
5     4  four
6     5  five
```

```r
str(df)
```

```
'data.frame':	10 obs. of  2 variables:
 $ digit: int  0 1 2 3 4 5 6 7 8 9
 $ name : chr  "zero" "one" "two" "three" ...
```


### SEE ALSO


```r
?str; ? head; ?tail
```

Factors
========================================================

A factor is a vector object used to specify a discrete classification
(grouping) of the components of other vectors of the same length.
R provides both ordered and unordered factors.


```r
options(digits = 3) # print only 3 digits
set.seed(1) # fixed randomization for rnorm
# simulate pm10 distribution
pm10 <- 10 ^ rnorm(100, 1.6, 0.27)
pm10 <- pm10[pm10 > 40] # higher values than 40 ug/m^3
set.seed(1) # fixed randomization for sample
regions <- c("mar", "ege", "kdz", "ica", "akd", "dga", "gda")
sta <- factor(sample(1:length(regions), length(pm10), replace = T))
levels(sta) <- regions
head(data.frame(sta, pm10))
```

```
  sta  pm10
1 ege  44.6
2 kdz 107.3
3 akd  48.9
4 gda  53.9
5 ege  63.0
6 gda  56.9
```

```r
tapply(pm10, sta, mean) # means by region
```

```
 mar  ege  kdz  ica  akd  dga  gda 
75.3 56.8 76.5 56.0 78.5 60.6 81.9 
```


### SEE ALSO


```r
?options; ?set.seed; ?runif; ?rnorm; ?sample; ?round; ?levels; ?tapply
```

Arrays
========================================================

- Vectors are one dimensional
- Matrices and data frames are two dimensional
- Arrays can hold more dimensions.
- Arrays can be consist of single type of data as matrices
- Indexing: array[row, column, ...]


```r
arr3d <- array(1:24, dim = c(4, 3, 2),
                dimnames = list(
                  c("one", "two", "three", "four"),
                  c("ein", "zwei", "drei"),
                  c("un", "deux")))
mat <- matrix(1:12, nrow = 4, byrow = TRUE,
              dimnames = list(
                c("one", "two", "three", "four"),
                c("ein", "zwei", "drei")))
```


```r
class(arr3d); class(mat) # class of object
length(arr3d); length(mat) # length of object
dim(arr3d); dim(mat) # dimensions
nrow(arr3d); nrow(mat) # number of rows
ncol(arr3d); ncol(mat) # number of columns
rownames(arr3d); rownames(mat)
colnames(arr3d); colnames(mat)
dimnames(arr3d); dimnames(mat)
```

### SEE ALSO

```r
?matrix; ?array; ?class; ?dim; ?nrow; ?ncol; ?rownames; ?colnames
```

Arrays
========================================================

## Indexing


```r
mat[1:2, 2:3]
```

```
    zwei drei
one    2    3
two    5    6
```

```r
mat[,2]
```

```
  one   two three  four 
    2     5     8    11 
```

```r
mat[,"zwei"]
```

```
  one   two three  four 
    2     5     8    11 
```

```r
class(mat[,2])
```

```
[1] "integer"
```

```r
class(mat[,2, drop = F])
```

```
[1] "matrix"
```

### SEE ALSO

```r
?drop
```

Arrays
========================================================

## Combining


```r
mat2 <- matrix(seq.int(2, 24, 2), nrow = 4,
               dimnames = list(
                 c("five", "six", "seven", "eight"),
                 c("vier", "funf", "sechs")))
rbind(mat, mat2)
```

```
      ein zwei drei
one     1    2    3
two     4    5    6
three   7    8    9
four   10   11   12
five    2   10   18
six     4   12   20
seven   6   14   22
eight   8   16   24
```

```r
cbind(mat, mat2)
```

```
      ein zwei drei vier funf sechs
one     1    2    3    2   10    18
two     4    5    6    4   12    20
three   7    8    9    6   14    22
four   10   11   12    8   16    24
```

### SEE ALSO

```r
?rbind; ?cbind; ?c
```


Arrays
========================================================

## Arithmetic


```r
mat + mat2
mat %*% c(1,2,3) # matrix multiplication
mat / mat2
t(mat) # transpose of the matrix
diag(mat)
diag(mat) <- 0 # set diagonal to zero
```

```
      ein zwei drei
one     3   12   21
two     8   17   26
three  13   22   31
four   18   27   36
```

```
      [,1]
one     14
two     32
three   50
four    68
```

```
       ein  zwei  drei
one   0.50 0.200 0.167
two   1.00 0.417 0.300
three 1.17 0.571 0.409
four  1.25 0.688 0.500
```

### SEE ALSO

```r
?t; ?aperm; ?diag; ?`%*%`; ?`%o%`
```

Lists and data frames
========================================================

- An object consisting of an ordered collection of objects
- There is no particular need for the components to be of the same mode or type


```r
Lst <- list(name = "John", wife = "Mary", no.children = 3,
            child.ages = c(4,7,9))
Lst$name # equal to Lst[[1]]
Lst[[4]] # equal to Lst$child.ages
Lst[["wife"]] # same as Lst$wife
names(Lst)
str(Lst)
```

```
[1] "John"
```

```
[1] 4 7 9
```

```
[1] "Mary"
```

```
[1] "name"        "wife"        "no.children" "child.ages" 
```

```
List of 4
 $ name       : chr "John"
 $ wife       : chr "Mary"
 $ no.children: num 3
 $ child.ages : num [1:3] 4 7 9
```

### SEE ALSO

```r
?list; ?names; ?str
```

Lists and data frames
========================================================

## Constructing and modifying lists


```r
Lst <- list(pm10 = pm10, region = sta)
str(Lst)
head(as.data.frame(Lst))
```

```
List of 2
 $ pm10  : num [1:53] 44.6 107.3 48.9 53.9 63 ...
 $ region: Factor w/ 7 levels "mar","ege","kdz",..: 2 3 5 7 2 7 7 5 5 1 ...
```

```
   pm10 region
1  44.6    ege
2 107.3    kdz
3  48.9    akd
4  53.9    gda
5  63.0    ege
6  56.9    gda
```

### SEE ALSO

```r
?list; ?str; ?as.data.frame
```

Lists and data frames
========================================================

## Concatenating lists

- An object consisting of an ordered collection of objects
- There is no particular need for the components to be of the same mode or type


```r
list.A <- list(name = "John", married = T, child.count = 3)
list.B <- list(name = "Jenny", married = F)
Lst <- c(list.A, list.B)
str(Lst)
head(as.data.frame(Lst))
Lst$name # which one? John or Jenny
```

```
List of 5
 $ name       : chr "John"
 $ married    : logi TRUE
 $ child.count: num 3
 $ name       : chr "Jenny"
 $ married    : logi FALSE
```

```
  name married child.count name.1 married.1
1 John    TRUE           3  Jenny     FALSE
```

```
[1] "John"
```

Lists and data frames
========================================================

## Making data frames


```r
df <- data.frame(pm10 = pm10, region = sta)
str(df)
head(df)
```

```
'data.frame':	53 obs. of  2 variables:
 $ pm10  : num  44.6 107.3 48.9 53.9 63 ...
 $ region: Factor w/ 7 levels "mar","ege","kdz",..: 2 3 5 7 2 7 7 5 5 1 ...
```

```
   pm10 region
1  44.6    ege
2 107.3    kdz
3  48.9    akd
4  53.9    gda
5  63.0    ege
6  56.9    gda
```

### SEE ALSO

```r
?list; ?str; ?as.data.frame
```

Reading data from files
========================================================

## read.table


```r
dt <- read.table("data.txt")
class(dt);str(dt)
```

```
[1] "data.frame"
```

```
'data.frame':	9 obs. of  5 variables:
 $ V1: int  100 200 300 400 500 600 700 800 900
 $ V2: chr  "a1" "a2" "a3" "a4" ...
 $ V3: chr  "b1" "b2" "b3" "b4" ...
 $ V4: logi  TRUE TRUE FALSE FALSE FALSE TRUE ...
 $ V5: chr  "x" "x" "x" "y" ...
```

```r
head(dt)
```

```
   V1 V2 V3    V4 V5
1 100 a1 b1  TRUE  x
2 200 a2 b2  TRUE  x
3 300 a3 b3 FALSE  x
4 400 a4 b4 FALSE  y
5 500 a5 b5 FALSE  y
6 600 a6 b6  TRUE  y
```

### SEE ALSO

```r
?read.table
```

Reading data from files
========================================================

## read.table


```r
dt <- read.table("data.txt", stringsAsFactors = T)
class(dt);str(dt)
```

```
[1] "data.frame"
```

```
'data.frame':	9 obs. of  5 variables:
 $ V1: int  100 200 300 400 500 600 700 800 900
 $ V2: Factor w/ 9 levels "a1","a2","a3",..: 1 2 3 4 5 6 7 8 9
 $ V3: Factor w/ 9 levels "b1","b2","b3",..: 1 2 3 4 5 6 7 8 9
 $ V4: logi  TRUE TRUE FALSE FALSE FALSE TRUE ...
 $ V5: Factor w/ 3 levels "x","y","z": 1 1 1 2 2 2 1 3 3
```

```r
head(dt)
```

```
   V1 V2 V3    V4 V5
1 100 a1 b1  TRUE  x
2 200 a2 b2  TRUE  x
3 300 a3 b3 FALSE  x
4 400 a4 b4 FALSE  y
5 500 a5 b5 FALSE  y
6 600 a6 b6  TRUE  y
```

### SEE ALSO

```r
?read.table; ?factor
```

Reading data from files
========================================================

## read.csv




```r
dt.pm10 <- read.csv("pm10.csv", sep = ";") # or use read.csv2
class(dt.pm10)
str(dt.pm10)
head(dt.pm10)
```

```
[1] "data.frame"
```

```
'data.frame':	43848 obs. of  6 variables:
 $ Date: chr  "2008-01-01 00:00:00" "2008-01-01 01:00:00" "2008-01-01 02:00:00" "2008-01-01 03:00:00" ...
 $ sta1: num  NA NA NA NA NA 18.1 NA 13.1 NA 28.2 ...
 $ sta2: num  36.6 30.5 33.3 NA 35 29.5 17 39.8 43.5 66.5 ...
 $ sta3: num  56.9 45.8 25.3 20.4 35.1 23.7 44 47.2 NA 38.4 ...
 $ sta4: num  NA NA NA NA NA NA NA NA NA NA ...
 $ sta5: num  51.6 40.4 78.9 39.4 54.6 24.3 16.8 NA 49.7 20.3 ...
```

```
                 Date sta1 sta2 sta3 sta4 sta5
1 2008-01-01 00:00:00   NA 36.6 56.9   NA 51.6
2 2008-01-01 01:00:00   NA 30.5 45.8   NA 40.4
3 2008-01-01 02:00:00   NA 33.3 25.3   NA 78.9
4 2008-01-01 03:00:00   NA   NA 20.4   NA 39.4
5 2008-01-01 04:00:00   NA 35.0 35.1   NA 54.6
6 2008-01-01 05:00:00 18.1 29.5 23.7   NA 24.3
```

### SEE ALSO

```r
?read.csv; ?read.csv2
```

Reading data from files
========================================================

## read.csv

Set column classes at first. But note that we lost the time information. Why?


```r
# Sys.setenv(TZ='GMT')
dt.pm10 <- read.csv("pm10.csv", sep = ";",
               colClasses = c("POSIXct", "numeric", "numeric",
                              "numeric", "numeric", "numeric"))
str(dt.pm10)
head(dt.pm10)
```

```
'data.frame':	43848 obs. of  6 variables:
 $ Date: POSIXct, format: "2008-01-01" "2008-01-01" ...
 $ sta1: num  NA NA NA NA NA 18.1 NA 13.1 NA 28.2 ...
 $ sta2: num  36.6 30.5 33.3 NA 35 29.5 17 39.8 43.5 66.5 ...
 $ sta3: num  56.9 45.8 25.3 20.4 35.1 23.7 44 47.2 NA 38.4 ...
 $ sta4: num  NA NA NA NA NA NA NA NA NA NA ...
 $ sta5: num  51.6 40.4 78.9 39.4 54.6 24.3 16.8 NA 49.7 20.3 ...
```

```
        Date sta1 sta2 sta3 sta4 sta5
1 2008-01-01   NA 36.6 56.9   NA 51.6
2 2008-01-01   NA 30.5 45.8   NA 40.4
3 2008-01-01   NA 33.3 25.3   NA 78.9
4 2008-01-01   NA   NA 20.4   NA 39.4
5 2008-01-01   NA 35.0 35.1   NA 54.6
6 2008-01-01 18.1 29.5 23.7   NA 24.3
```

Reading data from files
========================================================

## read.csv

Because dates are not UTC. Daylight saving is a problem.


```r
Sys.setenv(TZ='GMT')
dt.pm10 <- read.csv("pm10.csv", sep = ";",
               colClasses = c("POSIXct", "numeric", "numeric",
                              "numeric", "numeric", "numeric"))
# Sys.setenv(TZ='EET')
head(dt.pm10)
```

```
                 Date sta1 sta2 sta3 sta4 sta5
1 2008-01-01 00:00:00   NA 36.6 56.9   NA 51.6
2 2008-01-01 01:00:00   NA 30.5 45.8   NA 40.4
3 2008-01-01 02:00:00   NA 33.3 25.3   NA 78.9
4 2008-01-01 03:00:00   NA   NA 20.4   NA 39.4
5 2008-01-01 04:00:00   NA 35.0 35.1   NA 54.6
6 2008-01-01 05:00:00 18.1 29.5 23.7   NA 24.3
```


```r
dt.pm10$Date[2135:2140]
```

```
[1] "2008-03-29 22:00:00 GMT" "2008-03-29 23:00:00 GMT"
[3] "2008-03-30 00:00:00 GMT" "2008-03-30 01:00:00 GMT"
[5] "2008-03-30 02:00:00 GMT" "2008-03-30 03:00:00 GMT"
```

```r
Sys.setenv(TZ='EET')
dt.pm10$Date[2135:2140]
```

```
[1] "2008-03-30 00:00:00 EET"  "2008-03-30 01:00:00 EET" 
[3] "2008-03-30 02:00:00 EET"  "2008-03-30 04:00:00 EEST"
[5] "2008-03-30 05:00:00 EEST" "2008-03-30 06:00:00 EEST"
```

Reading data from files
========================================================

## read.csv

Another approach to date time objects


```r
dt.pm10 <- read.csv("pm10.csv", sep = ";")
# read date column as character
dt.pm10$Date <- strptime(dt.pm10$Date, "%Y-%m-%d %H:%M:%S")
head(dt.pm10)
dt.pm10$Date[2135:2141]
```

```
                 Date sta1 sta2 sta3 sta4 sta5
1 2008-01-01 00:00:00   NA 36.6 56.9   NA 51.6
2 2008-01-01 01:00:00   NA 30.5 45.8   NA 40.4
3 2008-01-01 02:00:00   NA 33.3 25.3   NA 78.9
4 2008-01-01 03:00:00   NA   NA 20.4   NA 39.4
5 2008-01-01 04:00:00   NA 35.0 35.1   NA 54.6
6 2008-01-01 05:00:00 18.1 29.5 23.7   NA 24.3
```

```
[1] "2008-03-29 22:00:00 EET"  "2008-03-29 23:00:00 EET" 
[3] "2008-03-30 00:00:00 EET"  "2008-03-30 01:00:00 EET" 
[5] "2008-03-30 02:00:00 EET"  "2008-03-30 03:00:00"     
[7] "2008-03-30 04:00:00 EEST"
```
This time you will loose timezone information at daylight saving transitions.

Reading data from files
========================================================

## Best practices

- Do not struggle with excel files. Save them as `.csv`, then read.
- Organize your csv file(s) before read.
- Try to fix all possible error.
- Convert your date-time information to `"%Y-%m-%d %H:%M:%S"` format.
- Save data as `.rds` file and load it by `readRDS` function.
- If you need to read similar multiple files, best create your own function
  to read.

Installing new R packages
========================================================

R has plenty of packages.


```r
install(rpart)
install(ggplot2)
```

Loading data from other R packages
========================================================

Almost all of the packages comes with their own sample data.


```r
data(package="rpart")
data(Puromycin, package="datasets")
?airquality
edit(airquality) # edit data if you need
```

If a package has been attached by library, its datasets are automatically included in the
search.

### SEE ALSO

```r
?data; ?save; ?dput; ?saveRDS; ?edit
```

Loops and control flow
========================================================

## Conditional execution: if statements


```r
if (expr_1) expr_2 else expr_3
```

The “short-circuit” operators && and || are often used as part of the
condition in an if statement. Whereas & and | apply element-wise to vectors,
&& and || apply to vectors of length one, and only evaluate their second
argument if necessary.


```r
age <- 12
if (age < 13) {
  print("Watch this with your Mom")
} else {
  print("Enjoy the movie!")
}
```

```
[1] "Watch this with your Mom"
```


```r
age <- 21
print(ifelse(age < 13, "Watch this with your Mom", "Enjoy the movie!"))
```

```
[1] "Enjoy the movie!"
```

### SEE ALSO

```r
?`if`; ?ifelse
```

Loops and control flow
========================================================

## for loops, repeat and while


```r
if (expr_1) expr_2 else expr_3
```

The “short-circuit” operators && and || are often used as part of the
condition in an if statement. Whereas & and | apply element-wise to vectors,
&& and || apply to vectors of length one, and only evaluate their second
argument if necessary.


```r
age <- 12
if (age < 13) {
  print("Watch this with your Mom")
} else {
  print("Enjoy the movie!")
}
```

```
[1] "Watch this with your Mom"
```


```r
age <- 21
print(ifelse(age < 13, "Watch this with your Mom", "Enjoy the movie!"))
```

```
[1] "Enjoy the movie!"
```

### SEE ALSO

```r
?`if`; ?ifelse
```
