# r-programming-assignments

Name: Sydney Claudio  
Course: LIS4370  

Description: Repository for R Programming Assignments.

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
