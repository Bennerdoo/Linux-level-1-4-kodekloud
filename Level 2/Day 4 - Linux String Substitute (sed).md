# Question

There is some data on Nautilus App Server 1 in Stratos DC. Data needs to be altered in several of the files. On Nautilus App Server 1, alter the /home/BSD.txt file as per details given below:


- a. Delete all lines containing word software and save results in /home/BSD_DELETE.txt file. (Please be aware of case sensitivity)
- b. Replace all occurrence of word and to them and save results in /home/BSD_REPLACE.txt file.


> Note: Let's say you are asked to replace word to with from. In that case, make sure not to alter any words containing the string itself; for example upto, contributor etc.

# Step-by-Step Solution

## 1. SSH into App Server 1

Use the credentials provided in your infrastructure details panel to SSH into App Server 1.

## 2. Delete Lines Containing the Word software

Use sed to delete (d) every line containing software (case-sensitive) and output the result to /home/BSD_DELETE.txt:

```Bash


sudo sed '/software/d' /home/BSD.txt | sudo tee /home/BSD_DELETE.txt > /dev/null

```

### Replace Whole Occurrences of and with them

Use sed with word boundary anchors (\b) to ensure words like stand or land are not altered, only exact matches of the word and:

```Bash


sudo sed 's/\band\b/them/g' /home/BSD.txt | sudo tee /home/BSD_REPLACE.txt > /dev/null
```

Verify the Results
Inspect the newly created files to confirm the transformations:

Bash


```Bash

# Check that no lines with 'software' remain in BSD_DELETE.txt
grep "software" /home/BSD_DELETE.txt

# Verify whole-word matches in BSD_REPLACE.txt
grep -w "them" /home/BSD_REPLACE.txt

```

> Note: Using `\b` creates a word boundary matching standard alphanumeric boundaries, ensuring substrings within words (e.g., contributor, upto) are preserved while replacing exact occurrences of and.