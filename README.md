# Neuger Email List Cleanup
This project provides helpful regular expressions that are commonly used to clean up email lists.

For those at Neuger, here is the private documentation:
http://wiki.neuger.com/wiki/HTML_Emails

## Cleaning Email Addresses
Open the CSV file in a text editor (preferably with the email address column as the first column) to test for two or more email addresses on the same line. If there are more than two on the same line, duplicate the current row for each email address on that line and make sure the information is the same (be careful of quotes).

Here are all the rules listed below combined:
`@.*@|[,;\(\)\[\]]| +|@.*?[^\.0-9a-z\r\-\n$].*?$|@[^\.]*$|\.\.|\.$|\.co?$|\.ne?$|\.or?$|\.ed?$|\.go?$`

In Excel, copy the email address column into a text editor, change them to lowercase and run the following regular expressions to identify potential invalid email addresses.

| Regular Expression         | Looks for                                                                                             |
|----------------------------|-------------------------------------------------------------------------------------------------------|
| @.*@                       | Searches for two "@" signs.                                                                           |
| [,;\(\)\[\]]               | Searches ,;()[] – invalid characters. These also might signify two email addresses in the same field. |
| \s+                        | Searches for spaces.                                                                                  |
| @.*?[^\.0-9a-z\r\-\n$].*?$ | Searches invalid characters after "@" sign.                                                           |
| @[^\.]*$                   | Searches for "." after "@".                                                                           |
| \.\.                       | Searches for two periods in a row.                                                                    |
| \.$                        | Searches for a "." at the end of the line.                                                            |
| \.co$                      | Searches for an email address ending in .co (also .ne, .or, .ed)                                      |
| \.c$                       | Searches for an email address ending in .c (also .n, .o, .e)                                          |
