## Examining a CSV generated from Facebook advertisers with my contact
## information after compiling country and industry information for each.

# Load required libraries

library(ggplot2)
library(dplyr)
library(tidyr)
library(stringr)

# Read in data

FB_Advertisers <- read.csv("Assume an Honest Facebook2.csv")

# Inspect Data

str(FB_Advertisers)

levels(FB_Advertisers)

summary(FB_Advertisers)

head(FB_Advertisers)

FB_Advertisers[!complete.cases(FB_Advertisers),]

unique(FB_Advertisers$Origin)

# Rename Columns to Something R Likes

colnames(FB_Advertisers) <- c("ID_Number", "Company Name", "Category", "Origin")

# Split out "Origin" from the data frame, determine proportion, and generate a
# simple plot.

PCT_Origin <- as.data.frame(prop.table(table(FB_Advertisers$Origin))*100)

PCT_Origin

colnames(PCT_Origin) <- c("Origin", "Percent of Advertisers")

PCT_Origin

P1 <- ggplot(PCT_Origin, aes(y = PCT_Origin$`Percent of Advertisers`, 
                             x = PCT_Origin$Origin)) + 
                     labs(y = "Percent of Advertisers", x = "Country") +
                     geom_bar(stat = "identity", fill = "blue") +
                     ggtitle("Percent of Advertisers by Country")

P1

# Split out "Category" from the data frame, determine proportion, and generate a
# simple plot.

PCT_Cat <- as.data.frame(prop.table(table(FB_Advertisers$Category))*100)

PCT_Cat

colnames(PCT_Cat) <- c("Industry", "Percent of Advertisers")

PCT_Cat

P2 <- ggplot(PCT_Cat, aes(y = PCT_Cat$`Percent of Advertisers`, 
                             x = PCT_Cat$Industry)) + 
        labs(y = "Percent of Advertisers", x = "Industry") +
        geom_bar(stat = "identity", fill = "green") +
        ggtitle("Percent of Advertisers by Industry") +
        scale_x_discrete(labels = function(x) str_wrap(x, width = 10)) +
        theme(axis.text.x = element_text(angle = 90, hjust = 1.0))

P2

## End
