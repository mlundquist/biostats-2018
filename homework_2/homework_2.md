
# Question 1

Consider two samples (male and female) of the 2006 Statistics class, using height data (see data in the previous slides),
calculate their means, medians, Q1, Q3, sample variances, and sample standard deviations.

This is pretty easily done by hand and in R

```r
    ## First read in the student height data from last week

    students <- read.csv("students.csv", h = T)
    students <- students[order(students$height), ] # Order heights shortest to tallest

    ## Subset to male and female

    m.students <- subset(students, students$sex == "M")
    f.students <- subset(students, students$sex == "F")

    ## Mean height
    mean(m.students$height) # 70.34 in
    mean(f.students$height) # 66.20 in

    ## Median height
    median(m.students$height) # 70 in
    median(f.students$height) # 65 in

    ## Quartiles
    ## Note: R calculates quartiles slightly differently than how Dr. Zhu and the book does
    ## Therefore, you should calculate them manually for the purpose of this class
    ## Rule : Rund subcript to nearest interger of half integer

    ## Male students

    m.X1 <- (length(m.students$height) + 1)/4
    m.X1 # 3.75 in
    m.q1 <- m.students$height[4] # We round 3.75 up to 4
    m.q1 # 67 in
    m.X3 <- length(m.students$height) + 1 - m.X1
    m.X3 # 11.25 in
    m.q3 <- m.students$height[11] # We round down to 11
    m.q3 # 73 in

    ## We can do this realtively easily in R
    quantile(m.students$height)
    ##  0%   25%   50%   75%  100%
    ## 67.00 67.25 70.00 72.75 75.00

    ## Q1 = 25% = 67.25 and Q3 = 75% = 72.75,
    ## Notice that the numbers are close but not exactly the same

    ## Female students

    f.X1 <- (length(f.students$height) + 1)/4
    f.X1 # 4 in
    f.q1 <- f.students$height[4] # We don't need to round
    f.q1 # 64 in
    f.X3 <- length(f.students$height) + 1 - f.X1
    f.X3 # 12 in
    f.q3 <- f.students$height[12] # No rounding here either
    f.q3 # 68 in

    ## We can do this realtively easily in R
    quantile(f.students$height)
    ##  0%   25%   50%   75%  100%
    ## 63.00 64.00 65.00 67.50 72.00

    ## Q1 = 25% = 64 and Q3 = 75% = 67.50,
    ## Notice that the numbers are close again but not exactly the same

    ## Sample variances
    ## Male
    m.SS <- sum((m.students$height - mean(m.students$height))^2) # Sum of squares
    m.SS # 113.21 in
    m.var <- m.SS / (length(m.students$height) - 1) # Variance
    m.var # 8.71 in

    ## Built-in var() function
    var(m.students$height) # 8.71 in

    ## Female
    f.SS <- sum((f.students$height - mean(f.students$height))^2) # Sum of squares
    f.SS # 98.4 in
    f.var <- f.SS / (length(f.students$height) - 1) # Variance
    f.var # 7.03 in

    ## Built-in var() function
    var(f.students$height) # 7.03 in

    ## Sample standard deviations
    ## Male
    m.sd <- sqrt(m.var)
    m.sd # 2.95 in

    ## Buld-in sd() function
    sd(m.students$height) # 2.95 in

    ## Female
    f.sd <- sqrt(f.var)
    f.sd # 2.65 in

    ## Buld-in sd() function
    sd(f.students$height) # 2.65 in

```

# Question 2

Exercises 4.1, 4.2, 4.3


```r
## 4.1

    x <- c(66.1, 77.1, 74.6, 61.8, 71.5) # Input data

    ## A
    ## Equation 4.12
    x.SS <-  sum((x - mean(x))^2) # Sum of squares
    x.SS # 156.03 g^2

    ## Equation 4.15
    x.var <- x.SS / (length(x) - 1) # Variance
    x.var # 39.0 g^2

    ## B
    ## Equation 4.16
    x.SS.2 <-  sum(x^2) - ((sum(x)^2) / length(x)) # Sum of squares
    x.SS.2 # 156.03 g^2

    ## Equation 4.17
    x.var.2 <- x.SS.2 / (length(x) - 1) # Variance
    x.var.2 # 39.0 g^2

    ## R check
    var(x) # 39.0 g^2


```

## 4.2

```r
    x <- c(240.6, 238.2, 236.4, 244.8, 240.7, 241.3, 237.9) # Input data
    x <- sort(x) # Order from smallest to largest

    ## A
    range_x <- x[length(x)] - x[1]
    range_x # 8.4 mg / 100 ml

    ## B
    x.SS <-  sum((x - mean(x))^2) # Sum of squares
    x.SS # 46.19 mg / 100 ml

    ## C
    x.var <- x.SS / (length(x) - 1) # Variance
    x.var # 7.70 mg / 100 ml

    ## D
    x.sd <- sqrt(x.var)
    x.sd # 2.77 mg / 100 ml

    ## E
    x.coef <- x.sd / mean(x)
    x.coef # 0.012 or 1.2%

    ## R check
    var(x) # 7.70
    sd(x) # 2.77
    sd(x) / mean(x) # 0.012 or 1.2%

```

## 4.3

```r
    trees <- read.csv("trees.csv", h = T) ## Load in tree data
    n <- sum(trees$frequency)
    n # 97
    p_i <- trees$frequency/n

    ## A (H')

    trees.H <- -1 * sum((p_i)*log10(p_i))
    trees.H # 0.595

    ## We can check this in R using the package vegan()
    ## install.packages("vegan") # Uncomment to install package
    library(vegan)
    ## We need to change the way the data is presented for vegan to be able to use it
    trees.t <- data.frame(t(trees[-1])) # Transpose second column to row and remove species
    colnames(trees.t) <- trees$species # Give each column the name of its corresponding species

    trees.H.vegan <- diversity(trees.t, base = 10) # Vegan function to calculate H', make sure to use proper log base
    trees.H.vegan # 0.595

    ## B (H' Max)
    k <- length(trees$species)
    trees.H.max <- log10(k)
    trees.H.max # 0.779

    ## C (J')
    trees.J <- trees.H / trees.H.max
    trees.J # 0.764

    ## Using vegan
    trees.J.vegan <- trees.H.vegan / log10(specnumber(trees.t))
    trees.J.vegan <- 0.764
```

# Question 3

A class has 22 Female White, 8 Male White,
2 Female Asian, 4 Male Asian, and 4 Female African American.
Calculate its Diversity Index and Evenness.

```r
    demo <- read.csv("demography.csv", h = T) ## Import class demography data

    ## We can look at this three ways

    ## 1) Diversity by student ethnicities

    student.ethnicity <- c(sum(demo$frequency[demo$ethnicity == "white"]),
                           sum(demo$frequency[demo$ethnicity == "asian"]),
                           sum(demo$frequency[demo$ethnicity == "african_american"])
                          )

    n <- sum(student.ethnicity)
    n # 40
    f <- student.ethnicity

    ethnicity.H <- (n*log10(n)- sum(f*log10(f))) / n
    ethnicity.H # 0.32

    k <- length(student.ethnicity)
    k # 3
    ethnicity.H.max <- log10(k)
    ethnicity.H.max # 0.48

    ethnicity.J <- ethnicity.H / ethnicity.H.max
    ethnicity.J # 0.69

    ## 2) Diversity by student sexes

    student.sex <- c(sum(demo$frequency[demo$sex == "f"]),
                           sum(demo$frequency[demo$sex == "m"])
                          )

    n <- sum(student.sex)
    n # 40
    f <- student.sex

    sex.H <- (n*log10(n)- sum(f*log10(f))) / n
    sex.H # 0.27

    k <- length(student.sex)
    k # 2
    sex.H.max <- log10(k)
    sex.H.max # 0.30

    sex.J <- sex.H / sex.H.max
    sex.J # 0.88

    ## 3) Diversity by ethnicity and sex

    student.both <- c(sum(demo$frequency[demo$ethnicity == "white" & demo$sex == "f"]),
                      sum(demo$frequency[demo$ethnicity == "white" & demo$sex == "m"]),
                      sum(demo$frequency[demo$ethnicity == "asian" & demo$sex == "f"]),
                      sum(demo$frequency[demo$ethnicity == "asian" & demo$sex == "m"]),
                      sum(demo$frequency[demo$ethnicity == "african_american" & demo$sex == "f"])
                      )

    n <- sum(student.both)
    n # 40
    f <- student.both

    both.H <- (n*log10(n)- sum(f*log10(f))) / n
    both.H # 0.55

    k <- length(student.both)
    k # 5
    both.H.max <- log10(k)
    both.H.max # 0.70

    both.J <- both.H / both.H.max
    both.J # 0.78
```
