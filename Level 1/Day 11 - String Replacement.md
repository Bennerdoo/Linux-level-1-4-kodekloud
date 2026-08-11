# Question

At xFusionCorp Industries, the Stratos Datacenter houses a jump host server that stores template XML files essential for the Nautilus application. Prior to their use, these files need to be populated with valid data. As part of regular maintenance, the system administration team utilizes various string and file manipulation commands to prepare these templates.


Your task is to substitute all occurrences of the string Text with Architecture within the XML file located at /root/nautilus.xml on the jump host server.

# Step-by-Step Solution

## Option 1: Using `sed` with In-Place Editing

### 1. Perform the Substitution
Use `sed` with the `-i` flag for in-place editing:
```Bash
sed -i 's/Text/Architecture/g' /root/nautilus.xml
```
- `-i`: Edits the file in-place.
- `s/Text/Architecture/`: Substitutes `Text` with `Architecture`.
- `g`: Global flag, replaces all occurrences on each line.

### 2. Verify the Change
Check the file content:
```Bash
cat /root/nautilus.xml
```
Or specifically look for the new string:
```Bash
grep Architecture /root/nautilus.xml
```

## Option 2: Using `sed` with a Backup (Safer)
If you want to keep a backup of the original file:
```Bash
sed -i.bak 's/Text/Architecture/g' /root/nautilus.xml
```
This creates `/root/nautilus.xml.bak` with the original content.

## Option 3: Using `awk`
```Bash
awk '{gsub(/Text/, "Architecture")}1' /root/nautilus.xml > /tmp/nautilus_new.xml && mv /tmp/nautilus_new.xml /root/nautilus.xml
```
- `gsub(/Text/, "Architecture")`: Performs global substitution.
- `1`: Prints every line.
- `> /tmp/... && mv`: Redirects to a temp file and then moves it to replace the original (safer than in-place for complex scripts).

## Option 4: Using `perl`
```Bash
perl -pi -e 's/Text/Architecture/g' /root/nautilus.xml
```
- `-p`: Loop through file and print lines.
- `-i`: In-place edit.
- `-e`: Execute script.

## Verification
After running any of the above commands, verify the result:
```Bash
speculoos@jump-host:~$ grep -c "Architecture" /root/nautilus.xml
# Expected output: A number > 0
```