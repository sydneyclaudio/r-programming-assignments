# r-programming-assignments

Name: Sydney Claudio  
Course: LIS4370 
Description: Repository for R Programming Assignments.

# Module 6 – Matrix Operations in R

#Step 1 is to create matrices A and B

A <- matrix(c(2,0,1,3), ncol = 2)
B <- matrix(c(5,2,4,-1), ncol = 2)

A
[,1] [,2]
[1,]    2    1
[2,]    0    3

B
[,1] [,2]
[1,]    5    4
[2,]    2   -1

dim(A)
[1] 2 2

dim(B)
[1] 2 2

#Find A + B
A+B
[,1] [,2]
[1,]    7    5
[2,]    2    2

#Find A - B
A - B
[,1] [,2]
[1,]   -3   -3
[2,]   -2    4

#Using the diag() function to build a matrix of size 4 with the following values 
#in the diagonal 4,1,2,3.

D <- diag(c(4,1,2,3))
D
[,1] [,2] [,3] [,4]
[1,]    4    0    0    0
[2,]    0    1    0    0
[3,]    0    0    2    0
[4,]    0    0    0    3

#Generate the following matrix
## [,1] [,2] [,3] [,4] [,5]
## [1,] 3 1 1 1 1
## [2,] 2 3 0 0 0
## [3,] 2 0 3 0 0
## [4,] 2 0 0 3 0
## [5,] 2 0 0 0 3

### Step 1:
M <- matrix(0, nrow = 5, ncol = 5)

### Step 2:
diag(M) <- c(3,3,3,3,3)

## Step 3:
M[1, ] <- c(3,1,1,1,1)

## Step 4:
M[2:5, 1] <- 2

## Final Result:
M
[,1] [,2] [,3] [,4] [,5]
[1,]    3    1    1    1    1
[2,]    2    3    0    0    0
[3,]    2    0    3    0    0
[4,]    2    0    0    3    0
[5,]    2    0    0    0    3


Module # 5 Doing Math

# Create Matrix A (10x10)
A <- matrix(1:100, nrow = 10)

# Create Matrix B (10x100)
B <- matrix(1:1000, nrow = 10)

# View matrices
A
B

# Determinant of A
det_A <- det(A)
det_A

# Inverse of A
inv_A <- solve(A)


Module # 4 Programming structure assignment RStudio code
# Create vectors

Freq <- c(0.6,0.3,0.4,0.4,0.2,0.6,0.3,0.4,0.9,0.2)
bloodp <- c(103,87,32,42,59,109,78,205,135,176)
#bad=1 good=0
First <- c(1,1,1,1,0,0,0,0,NA,1)
#low=0 high=1
Second <- c(0,0,1,1,0,0,1,1,1,1)
#low=0 high=1
FinalDecision <- c(0,1,0,1,0,1,0,1,1,1) 

#Combining data into a dataframe

hospital_data <- data.frame(
  Freq,
  bloodp,
  First,
  Second,
  FinalDecision
)

#Creating a side-by-side boxplot and histogram

par(mfrow=c(1,2))

boxplot(bloodp,
        main="Boxplot of Patient Blood Pressure",
        ylab="Blood Pressure")

hist(bloodp,
     main="Histogram of Patient Blood Pressure",
     xlab="Blood Pressure")


## Module # 2 Assignment Blog Post

Blog post explaining debugging and correcting the `myMean` function:  
https://sydneyclaudiousf.blogspot.com/2026/01/module-2-assignment.html

## Corrected myMean Function
> assignment2 <- c(16, 18, 14, 22, 27, 17, 19, 17, 17, 22, 20, 22)
> myMean <- function(assignment2) {
+     sum(assignment2) / length(assignment2)
+ }
> myMean(assignment2)
