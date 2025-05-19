This is a fork from CRAN/BOIN read-only repo.

The goal of this repo is to 
* add/mimic certain functions implemented by the BOIN in the  trialdesign.org but not available in the R CRAN BOIN package yet.
* make modification according to drug development business needs.

The fork starts with BOIN 2.7.2 in May 2024. 

run the following to install this updated BOIN package.

```r
install.packages("devtools")
devtools::install_github("https://github.com/OliviaClare/BOIN-AT")
library(BOIN)
```

Updates:
* Add a logical argument fix3p3 in get.oc and get.boundary to implement 3+3 mimic, including
	* If none of the phi's and lambda's are specified, use the original logic, phi1 = 0.6 * phi, phi2 = 1.4 * phi, then calculate lambda1 and lambda2
	* If phi1 and phi2 are specified, calculate lambda1 and lambda 2
	* If lambda1 and lambda2 are specified, calculate phi1 and phi2
	* If all are specified, use lambda1 and lambda2, calculate phi1 and phi2, issue a warning message.

* When calculating the percentage of simulation trials that lead to overdosing X% of patients (X = 50, 60, 80), relax the previous requirement that target DLT needs to be one of the dose level in simulation, i.e., removing the logical test that "if (length(which(p.true == target)) > 0)" in get.oc.R.
