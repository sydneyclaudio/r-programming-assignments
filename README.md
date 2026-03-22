# r-programming-assignments

Name: Sydney Claudio  
Course: LIS4370 
Description: Repository for R Programming Assignments.

# Assignment #9
# Visualization in R – Base Graphics, Lattice, and ggplot2

# Load dataset
data("iris", package = "datasets")
head(iris)

# Base R Graphics

# Scatter plot
plot(iris$Sepal.Length, iris$Petal.Length,
     main = "Base R: Sepal Length vs Petal Length",
     xlab = "Sepal Length",
     ylab = "Petal Length",
     col = as.numeric(iris$Species),
     pch = 19)

# Histogram
hist(iris$Sepal.Width,
     main = "Base R: Distribution of Sepal Width",
     xlab = "Sepal Width",
     col = "lightgray",
     border = "white")


# Lattice Graphics

library(lattice)

# Conditioned scatter plot
xyplot(Petal.Length ~ Sepal.Length | Species,
       data = iris,
       main = "Lattice: Petal Length vs Sepal Length by Species",
       xlab = "Sepal Length",
       ylab = "Petal Length")

# Box plot
bwplot(Sepal.Width ~ Species,
       data = iris,
       main = "Lattice: Sepal Width by Species",
       xlab = "Species",
       ylab = "Sepal Width")


# ggplot2

library(ggplot2)

# Scatter plot with smoothing
ggplot(iris, aes(x = Sepal.Length, y = Petal.Length, color = Species)) +
  geom_point() +
  geom_smooth(method = "lm", se = FALSE) +
  labs(title = "ggplot2: Petal Length vs Sepal Length by Species",
       x = "Sepal Length",
       y = "Petal Length")

# Faceted histogram
ggplot(iris, aes(x = Sepal.Width)) +
  geom_histogram(binwidth = 0.2) +
  facet_wrap(~ Species) +
  labs(title = "ggplot2: Sepal Width Distribution by Species",
       x = "Sepal Width",
       y = "Count")

# Module 8 - Input/Output, String Manipulation,
# Install/load package
install.packages("plyr")
library(plyr)

# Step 1: Import dataset
x <- read.table(file.choose(), header = TRUE, sep = ",")

# View data
x

# Find mean Grade by Sex using plyr
students_gendered_mean <- ddply(x, "Sex", transform,
                                +                                 Grade.Average = mean(Grade))
# Write output to a file
write.table(students_gendered_mean, "Students_Gendered_Mean", sep = ",")

# Step 2: Filter names containing the letter i
i_students <- subset(x, grepl("i", x$Name))
i_students

# Step 3: Write filtered dataset to CSV
write.table(i_students, "Students_With_I.csv", sep = ",", row.names = FALSE)

# OO Systems in R – S3 and S4 Example

#Load dataset
data("mtcars")

#S3 Example

student <- function(n, a, g) {
  if (g > 4 || g < 0)
    stop("GPA must be between 0 and 4")

  value <- list(name = n, age = a, GPA = g)
  attr(value, "class") <- "student"
  value
}

print.student <- function(x) {
  cat("Student:", x$name,
      "| Age:", x$age,
      "| GPA:", x$GPA, "\n")
}

s <- student("Paul", 26, 3.7)
s

#S4 Example
library(methods)

setClass(
  "studentS4",
  slots = c(
    name = "character",
    age = "numeric",
    GPA = "numeric"
  )
)

s4 <- new("studentS4",
          name = "John",
          age = 21,
          GPA = 3.5)

s4

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
