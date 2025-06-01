# Load necessary libraries
library(readr)
library(ggplot2)

# Set working directory (update if needed)
setwd("C:/Users/Komal/Desktop/DAproject")

# Read the dataset
myData <- read_csv("rating.csv")

# Initial exploration of the dataset
head(myData)
tail(myData)
str(myData)
summary(myData)

# --- Histogram: Ratings Distribution ---
print(ggplot(data = myData, aes(x = rating)) +
        geom_histogram(binwidth = 0.5, color = "blue", fill = "lightblue") +
        ggtitle("Histogram of Ratings") +
        xlab("Ratings") +
        ylab("Number of Ratings") +
        theme(axis.title.x = element_text(color = "red", size = 15),
              axis.title.y = element_text(color = "purple", size = 15),
              plot.title = element_text(color = "red", size = 15)))

# --- Scatter Plot: Rating vs Timestamp ---
print(ggplot(data = myData, aes(x = timestamp, y = rating)) +
        geom_point(color = "purple") +
        ggtitle("Scatter plot of Rating vs Timestamp") +
        xlab("Timestamp") +
        ylab("Rating") +
        theme(axis.title.x = element_text(color = "red", size = 15),
              axis.title.y = element_text(color = "purple", size = 15),
              plot.title = element_text(color = "red", size = 15)))

# --- Boxplot for Ratings ---
print(ggplot(data = myData, aes(x = factor(1), y = rating)) +
        geom_boxplot(fill = "lightgreen") +
        ggtitle("Boxplot of Ratings") +
        xlab("Ratings") +
        ylab("Rating Value") +
        theme(axis.title.x = element_text(color = "red", size = 15),
              axis.title.y = element_text(color = "purple", size = 15),
              plot.title = element_text(color = "red", size = 15)))

# --- Histogram: Rating Distribution for Each Movie ---
# Filtering dataset to a smaller subset of movieIds for testing
myData_small <- myData[myData$movieId <= 10, ]  # Limit to movieId 1 to 10 for test
print(ggplot(data = myData_small, aes(x = rating, fill = factor(movieId))) +
        geom_histogram(binwidth = 0.5, color = "black") +
        facet_wrap(~ movieId) +
        ggtitle("Histogram for Ratings by Movie") +
        xlab("Ratings") +
        ylab("Total Number of Ratings") +
        theme(axis.title.x = element_text(color = "red", size = 15),
              axis.title.y = element_text(color = "purple", size = 15),
              plot.title = element_text(color = "red", size = 15)))
