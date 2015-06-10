# williams-test

Instructions for Williams Significance Test
-----------------------------------------------------------------------------------

Contact: graham.yvette@gmail.com

-----------------------------------------------------------------------------------

The following is a description of how to carry out significance tests for an
increase in Pearson correlation of one metric (or QE system) over that of a baseline 
metric (or baseline QE system) and is described further in the following papers:

Yvette Graham & Timothy Baldwin. "Testing for Significance of Increased Correlation 
with Human Judgment", EMNLP 2014.

Yvette Graham, Timothy Baldwin, Nitika Mathur. "Accurate Evaluation of
Segment-level Machine Translation Metrics", NAACL 2015.

Yvette Graham. "Improving Evaluation of Machine Translation Quality Estimation", ACL
2015.

Requirements:
--------------------

1. "R Statistical Software"
    - To install R on the command line:
          > sudo apt-get install r-base

2. R's "psych" package

      To install R's "psych" package:
         - IF your institution uses a proxy server, you need to tell R about it BEFORE
           installing any package, here's what to do:
           A) Open your R command line, by typing "R"
           B) Type the following commmand into R, remembering to provide your
              actual credentials and proxy server details:

           > Sys.setenv(http_proxy="http://myusername:mypasssord@myproxyserver.com:8080/")

           IF NOT, continue on below.

         - Open R command line (by typing "R") and enter the following:

           > install.packages("psych")

           You'll be given an option of a CRAN site, when you have one selected, you
           might need to answer "y" to some questions. When "psych" is finished
           installing, type the following to quit R:

            > quit("no")


How to run:
--------------------

Run one-sided application of Williams Test to test the significance of the increase in 
correlation between r12 and r13 below, with sample size n:
- r12: Human scores and Metric A, 
- r13: Human scores and Metric B,
- r23: Metric A and Metric B 

     R --no-save --args \<r12\> \<r13\> \<r23\> \<n\> < williams.R

This returns the p-value for the test that r12 is greater than r13.

For example, Williams test with the following:

     R --no-save --args 0.65 0.55 0.3 50 < williams.R

Will produce the following output:

    Williams Test for Increase in Correlation 

        r12 correlation( human, metric_a ) :  0.65 
        r13 correlation( human, metric_b ) : 0.55 
        r23 correlation( metric_a, metric_b) : 0.3 
        Sample size: 50 

    P-value: 0.209243482964009 

Since p > 0.05, the increase in correlation is not significant. 
