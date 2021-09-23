# STAT-433-HW_2

## Problem 1
library(dplyr)
bridges_data <- read.csv("bridges_data.txt", header=TRUE, sep=",", dec=".")

bridge <- bridges_data[c("STRUCTURE_NUMBER_008", "STATE_CODE_001", "YEAR_BUILT_027", "DECK_COND_058", "SUPERSTRUCTURE_COND_059", "CHANNEL_COND_061")]

bridge = bridge[bridge$YEAR_BUILT_027 > 1870, ]
hist(bridge$YEAR_BUILT_027, main="Year-Built", xlab="Year")

hist(as.integer(bridge$STATE_CODE_001), main="State Code", xlab="state code")

bridge = bridge[bridge$DECK_COND_058 != "N",]
hist(as.integer(bridge$DECK_COND_058), main="Bridge quality", xlab="Bridge quality")


## Problem 2
require(rvest)
site = read_html("https://guide.wisc.edu/faculty/")
text = html_text(html_nodes(site, "p"))
text = text[3:3792]
text
