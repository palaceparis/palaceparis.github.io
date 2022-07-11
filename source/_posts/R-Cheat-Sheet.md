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

# html_nodes, html_attr, str_c

Extract href and remove the link in str_c

```
        remDr$getPageSource()[[1]] %>%      
          read_html() %>%      
          html_nodes(".lean-table-cell a") %>%      
          html_attr('href') %>%    
          str_c("https://broker.skyallmarkets.com", .)    
```