---
title: R Cheat Sheet
category: Other
tags:
  - 'R'
  - 'RStudio'
  - 'Coding'
date: 2022-07-11 19:19:28
description: "R cheat sheet"
---

# here, read_csv

Clean directory with data in a specific folder

`read_csv(here("data", "SummaryReport_20220518003802.csv")) %>% janitor::clean_names()`

# str_sub

Extract characters according to position number and match

`str_sub(sales_admin, start = 1, end=4)=="Mark")`

# read_excel

`read_excel(here("data", "login.xlsx")) %>% janitor::clean_names()`

# write.xlsx

`write.xlsx(acc_raw5, "acc_raw5.xlsx", sheetName = "Sheet1", col.names = TRUE, row.names = FALSE, append = FALSE)`

# list_versions

Use when rsDriver cannot run.

`binman::list_versions("chromedriver")`

#  webElem1 <- remDr$findElement(using = "name", value = "q")

Locate the search box on google search page

# webElem1$clearElement() 

clear the text previously entered

# webElem1$sendKeysToElement(list("R", key = "enter"))

Input and hit

# findElements and sapply

Retrieve data from website using **Value** only to locate in findElements.

Example as below:

```
googLinkText <- remDr$findElements(value = "//h3[@class = 'LC20lb MBeuO DKV0Md']")
linkHeading <- sapply(googLinkText, function(x) x$getElementText())
googLinkDesc <- remDr$findElements(value = "//div[@class = 'VwiC3b yXK7lf MUxGbd yDYNvb lyLwlc lEBKkf']")
linkDescription <- sapply(googLinkDesc, function(x) x$getElementText())
googLinkHref <- remDr$findElements(value = "//div[@class = 'yuRUbf']/a")
linkHref <- sapply(
googLinkHref,
function(x) x$getElementAttribute("href")
)
```

# rD[["server"]]$stop()

Reset browser port

# getChromeProfile and rsDriver

Launch the dafault chrome browser

Example as below: 

```
cprof <- getChromeProfile(
"/Users/tonygong/Library/Application Support/Google/Chrome",
"Profile 1"
)
rD <- rsDriver(browser = "chrome", port = 1624L, chromever = "102.0.5005.61", extraCapabilities = cprof)
remDr <- rD$client
remDr$navigate("https://my.skyamarkets.com/Admin/login?ReturnUrl=%2FSuperAdmin%2FClients")
```

# html_nodes, html_attr, str_c

Extract href and remove the link in str_c

```
        remDr$getPageSource()[[1]] %>%      
          read_html() %>%      
          html_nodes(".lean-table-cell a") %>%      
          html_attr('href') %>%    
          str_c("https://broker.skyallmarkets.com", .)    
```

Task_images_pdf