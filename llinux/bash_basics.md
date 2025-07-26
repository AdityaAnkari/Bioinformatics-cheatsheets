
# 🖥️ Bash Basics for Bioinformatics

This cheatsheet covers essential Bash commands every bioinformatics beginner should know.  
Bash is the command-line interface used to interact with Linux-based systems — it's how most bioinformatics work is done behind the scenes.

---

## 📌 Why Learn Bash?

- 💻 Control your computer without a mouse
- 📁 Navigate large folders of FASTQ, BAM, VCF files easily
- 🔄 Automate repetitive tasks
- ⚙️ Run pipelines like `Snakemake`, `Nextflow`, or `bash` scripts

---

## 🧭 Getting Started

### ✅ Open a Terminal

| OS | How to open |
|----|-------------|
| Windows | Use **Git Bash** or **WSL (Windows Subsystem for Linux)** |
| macOS | Open the **Terminal** app |
| Linux | Press `Ctrl + Alt + T` or use any terminal |

---

## 📂 Navigating Files and Folders

| Command | Description |
|---------|-------------|
| `pwd` | Print current folder path |
| `ls` | List files in the folder |
| `ls -lh` | List with file sizes and details |
| `cd foldername/` | Change into a folder |
| `cd ..` | Go back one level |
| `mkdir newfolder` | Make a new folder |
| `rm file.txt` | Delete a file |

### 🧪 Example
```bash
mkdir genome_project
cd genome_project
touch sample.txt
ls
### 📄 Viewing File Content


| Command          | Description                             |
| ---------------- | --------------------------------------- |
| `cat file.txt`   | Show whole file                         |
| `less file.txt`  | Scroll through file (press `q` to quit) |
| `head file.txt`  | First 10 lines                          |
| `tail file.txt`  | Last 10 lines                           |
| `wc -l file.txt` | Count number of lines                   |

Example:
echo "This is a test line" > test.txt
cat test.txt

**grep is used to search inside files.**
grep "gene" annotations.gff

**Pipes & Redirects**
Symbol	Function
>	Redirect output to a new file
>>	Append output to a file

**Examples:**
bash
Copy code
cat file.txt | grep "chr1" > chr1_genes.txt

**Loops – Repeat Commands for Many Files**

for file in *.fastq
do
  echo "Processing $file"
done

**Helpful Shortcuts**
| Shortcut   | Function                     |
| ---------- | ---------------------------- |
| `Tab`      | Autocomplete filename/folder |
| `Ctrl + C` | Stop running command         |
| `Ctrl + L` | Clear terminal               |
| `history`  | Show command history         |
| `!!`       | Run previous command again   |

**Practice Tasks
Try these:**

**Make a new folder and enter it:**

mkdir test_project && cd test_project
Create 3 text files:

Create 3 text files:

**Create 3 text files**

echo "apple" > file1.txt
echo "banana" > file2.txt
echo "apple banana" > file3.txt

**Count how many files mention "apple":**

grep -i "apple" *.txt | wc -l

📚 Learn More 
🔗 Learn Bash Online (https://ryanstutorials.net/bash-scripting-tutorial/)

📘 Cheat Sheet PDF (https://devhints.io/bash)

📦 Install Bash on Windows (WSL) (https://learn.microsoft.com/en-us/windows/wsl/install)

**TL;DR: Quick Bash Cheatsheet**

# Navigation
pwd && ls && cd folder/ && cd ..

# Files
mkdir data && touch file.txt && rm file.txt

# Viewing content
cat file.txt && head file.txt && tail file.txt

# Search & filter
grep "pattern" file.txt && wc -l file.txt

# Loops
for f in *.fastq; do echo $f; done

# Redirection
command > out.txt && command | another_command


## ✅ What To Do Now

1. Go to your GitHub repo: `bioinformatics-cheatsheets`
2. Navigate to the folder: `linux/`
3. Click **"Add file" → "Create new file"**
4. Name it: `bash_basics.md`
5. Paste the entire markdown above
6. Commit the file: `"Add bash_basics.md cheatsheet"`



