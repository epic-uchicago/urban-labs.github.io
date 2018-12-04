# Instructions on Setting up a Cron Job

## For .R file:
Inside terminal/shell prompt:
   - To edit or create a cron job, type command `crontab –e`
   - Define cron job using syntax: 
```
* * * * * Rscript “/path/to/file.R”
|   |  |  |  |
|   |  |  | ----- Day of week (0 - 7) (Sunday=0 or 7)
|   |  | ------- Month (1 - 12)
|   | --------- Day of month (1 - 31)
| ----------- Hour (0 - 23)
------------- Minute (0 - 59)
```
(asterisk means “every”)
   - Example:
`30 22 * * 1` means every Monday at 22:30, regardless of the date


## For knitting .Rmd file:
   - Create a .R file:
```
library(rmarkdown)
rmarkdown :: render ( input = "file.Rmd”
                      , output_format = "pdf_document"
                      , output_file = "file.pdf"
                      , output_dir = NULL)
```
   - Inside terminal:
Schedule cron to run .R file like above


## Useful commands and tips:
   - To display the current crontab: `crontab –l`
   - To remove the current crontab: `crontab -r`
   - To use command-line text editor nano: `export VISUAL=nano; crontab –e`
   - To email output to an email account, define MAILTO variable before the cron job line: `MAILTO = “…@...”`
       - To email multiple recipients, separate email addresses by coma, and do NOT include space
   - To disable email out, append at the end of the cron job line: `>/dev/null 2>&1`
   - A format example:
   ```
MAILTO = “a@uchicago.edu,b@uchicago.edu,c@uchicago.edu”
0 17 30 * * RScript “/export/…/file.R” >/dev/null 2>&1
```
This means at 5p.m. on the 30th of every month, run the .R file. Notice output email to recipients is disabled.


## Resources for more details and relevant crontab commands:
   - https://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/
   - https://www.computerhope.com/unix/ucrontab.htm
   - https://www.tutorialspoint.com/unix_commands/crontab.htm
