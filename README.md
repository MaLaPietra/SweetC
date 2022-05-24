# SweetC

library(conflictPower)
library(kableExtra)
library(dplyr)

mu <- c(625.4,732.4)
sigma <- c(68.6,80.7)
tau <- c(166.3,157.5)
flanker <- data.frame(mu,sigma,tau)
row.names(flanker) <- c("no conflict","conflict")
knitr::kable(flanker)

c_power_fast(subjects=20,
             c_nmst = c(50,732.4,80.7,157.5),
             nc_nmst = c(50,625.4,68.6,166.3),
             num_sims = 10000,
             alpha = .05)
             
pwr.out <- c_power_table(subjects = c(10,20,30,40,50),
              differences = c(10,20,30,40,50),
              c_nmst = c(50,732.4,80.7,157.5),
              nc_nmst = c(50,625.4,68.6,166.3),
              num_sims = 100,
              alpha = .05)

kable(pwr.out$power_table) %>%
  kable_styling() %>%
  scroll_box(width = "500px", height = "400px")
  
