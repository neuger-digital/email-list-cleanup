# Neuger Email List Cleanup
This project provides helpful regular expressions that are commonly used to clean up email lists.

For those at Neuger, here is the private documentation:
http://wiki.neuger.com/wiki/HTML_Emails

## Cleaning Email Addresses
Copy the email column into a text editor, convert the emails to lowercase `⌘K, ⌘L` and search for the following regular expressions to identify potential invalid emails.

| Regular Expression         | Looks for                                                                                                     |
|----------------------------|---------------------------------------------------------------------------------------------------------------|
| @.*@                       | Searches for two `@@` signs.                                                                                   |
| [,;\\(\\)\\[\\]]               | Searches `,;()[]` – invalid characters. These also might signify two email addresses in the same field.       |
| \s+                        | Searches for spaces.                                                                                          |
| @.*?[^\\.0-9a-z\\r\\-\\n$].*?$ | Searches invalid characters after `@` sign.                                                                   |
| @[^\\.]*$                   | Searches for `.` after `@`.                                                                                   |
| \\.\\.                       | Searches for two periods `..` in a row.                                                                       |
| \\.$                        | Searches for a `.` at the end of the line.                                                                    |
| \\.co$                      | Searches for an email address ending in `.co` (also `.ne`, `.or`, `.ed`)                                      |
| \\.c$                       | Searches for an email address ending in `.c` (also `.n`, `.o`, `.e`)                                          |

To make things easier, all of these can be combined into a singular regular expression to search for common email list issues.

| Combined Regular Expression                                                                                     |
|-----------------------------------------------------------------------------------------------------------------|
| ```@.*@\|[,;\(\)\[\]]\| +\|@.*?[^\.0-9a-z\r\-\n$].*?$\|@[^\.]*$\|\.\.\|\.$\|\.co?$\|\.ne?$\|\.or?$\|\.ed?$\|\.go?$``` |
