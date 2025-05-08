---
title: Taming the Beast, How I Handled a 1GB CSV File with a Simple Bash Script
date: 2025-04-29 20:14 +0300
categories: [Blogging, ITTricks, LifeStyle]
tags: [blog,Bash,Split,CSV, LifeinIT,]
author: Dinusha Tharindu
---



## 👇 The Problem

Not long ago, I was deep into an access review project for a client. The task was straightforward on paper: pull a list of who had access to what across a large repository of internal documents.

After aggregating logs and generating the report, I exported the data into a CSV file. But there was a catch.

The file was **almost 1GB** in size.

I quickly realized I had a problem when my usual tools — Excel, VS Code, Notepad++ — all failed to open the file. Excel froze, editors crashed, and I couldn’t even scroll through a few lines to verify what I had. I was effectively locked out of my own data.

---

## 🔍 The Discovery

I knew there had to be a better way, so I turned to something I hadn't used in a while: the terminal.

After a bit of research and experimentation, I found a reliable method using classic Unix tools like `split` and `mv` to break the massive CSV file into smaller, more manageable pieces. Then I packaged the whole process into a simple Bash script for future use.

---

## 🛠️ The Solution — A Bash Script to Split Large CSVs

Here's the script that saved the day — and continues to serve me well:

```
bash
#!/bin/bash

# ----------------------------
# Split a large CSV file into smaller chunks
# Usage: ./split_csv.sh filename.csv [size|lines] [value]
# Example: ./split_csv.sh bigfile.csv size 100m
#          ./split_csv.sh bigfile.csv lines 415000
# ----------------------------

set -e

if [ "$#" -ne 3 ]; then
    echo "Usage: $0 filename.csv [size|lines] [value]"
    echo "Example: $0 bigfile.csv size 100m"
    echo "         $0 bigfile.csv lines 415000"
    exit 1
fi

FILENAME="$1"
MODE="$2"
VALUE="$3"

if [ ! -f "$FILENAME" ]; then
    echo "Error: File '$FILENAME' not found."
    exit 1
fi

echo "Cleaning old split files..."
rm -f x* *.csv.part

if [ "$MODE" = "size" ]; then
    echo "Splitting '$FILENAME' into chunks of size $VALUE..."
    split -b "$VALUE" "$FILENAME"
elif [ "$MODE" = "lines" ]; then
    echo "Splitting '$FILENAME' into chunks of $VALUE lines each..."
    split -l "$VALUE" "$FILENAME"
else
    echo "Error: Unknown mode '$MODE'. Use 'size' or 'lines'."
    exit 1
fi

echo "Renaming split files..."
for f in x*; do
    mv "$f" "$f.csv.part"
done

echo "Done! Split files saved as *.csv.part"


```
