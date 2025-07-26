# 🔁 Snakemake – Introduction to Workflow Automation

**Snakemake** is a workflow management system that helps you automate complex pipelines in bioinformatics.  
It ensures that:

- Each step runs in the right order  
- Files are created only when needed  
- Work can resume after interruption  
- You don’t repeat manual steps again and again

Snakemake is like a smart lab assistant — it remembers everything and does all the work *exactly* the way you want.

---

## 🧾 What Is This Page?

This cheatsheet teaches you:

- What Snakemake is and why it's important
- How to install and set up Snakemake
- How to write your **first Snakefile**
- How rules, input/output, and wildcards work
- How to run workflows on your PC or cluster
- Common mistakes and how to fix them

No programming background needed. Everything is explained for total beginners.

---

## 💻 Why Use Snakemake?

| Problem | Snakemake Solves It |
|--------|----------------------|
| Manually running each command? | Automates it |
| Forgetting what steps you did? | Tracks everything |
| Rerunning all steps again? | Runs only what's missing |
| Messy scripts with copy-paste? | Keeps your pipeline clean |
| Submitting jobs to a cluster? | Has built-in support |

---

## 🧪 Installation

### ✅ Using Conda (Recommended)

```bash
conda create -n snakemake -c bioconda -c conda-forge snakemake
conda activate snakemake


Test it:

```bash

snakemake --help

📁 Project Structure
Let’s assume you’re analyzing FASTQ files with fastqc and bwa.

Example folder:

project/
├── data/
│   ├── sample1_R1.fastq.gz
│   └── sample1_R2.fastq.gz
├── results/
├── Snakefile
└── config.yaml

🐍 Your First Snakefile
```python

rule all:
    input:
        "results/sample1_fastqc.html"

rule fastqc:
    input:
        "data/sample1_R1.fastq.gz"
    output:
        "results/sample1_fastqc.html"
    shell:
        "fastqc {input} --outdir results"

▶️ How to Run It
```bash

snakemake -j 1
-j 1 = use 1 core/thread

Snakemake checks what files exist and what needs to run

🧠 Key Concepts

| Concept     | Meaning                               |
| ----------- | ------------------------------------- |
| `rule`      | A pipeline step (like FastQC or BWA)  |
| `input`     | File(s) required for the rule to run  |
| `output`    | File(s) created by the rule           |
| `shell`     | The actual command being run          |
| `wildcards` | Dynamic filenames (like sample names) |
| `rule all:` | Final result(s) you want produced     |

⚡ Wildcards Example (for multiple samples)
```python

SAMPLES = ["sample1", "sample2"]

rule all:
    input:
        expand("results/{sample}_fastqc.html", sample=SAMPLES)

rule fastqc:
    input:
        "data/{sample}_R1.fastq.gz"
    output:
        "results/{sample}_fastqc.html"
    shell:
        "fastqc {input} --outdir results"


Now Snakemake will loop over both samples!

🧰 Real Bioinformatics Examples

| Task            | Tool                 | Snakemake Usage                    |
| --------------- | -------------------- | ---------------------------------- |
| Quality Control | FastQC               | Run for all FASTQ files            |
| Alignment       | BWA                  | Automatically align all samples    |
| Trimming        | fastp                | Only run for untrimmed reads       |
| Variant Calling | bcftools             | Link BAM → BCF → VCF steps         |
| T2T Assembly    | Hifiasm, Purge\_dups | Automate every step and checkpoint |

📚 Useful Snakemake Commands
| Command               | What it does                     |                           |
| --------------------- | -------------------------------- | ------------------------- |
| `snakemake -j 1`      | Run workflow using 1 core        |                           |
| `snakemake -np`       | Show what will run (dry run)     |                           |
| \`snakemake --dag     | dot -Tpdf > dag.pdf\`            | Generate workflow diagram |
| `snakemake --summary` | Show status of each rule         |                           |
| `snakemake --unlock`  | Unlock folder if run interrupted |                           |


🧪 Try It Yourself: Mini Demo

1.Create this folder structure:

```bash

mkdir snakemake_test
cd snakemake_test
mkdir data results

2.Download sample data:

```bash

wget -O data/sample1_R1.fastq.gz https://raw.githubusercontent.com/jake-andrews/bwa-mini-example/main/reads.fastq

3.Create a file Snakefile with the basic FastQC rule

4.Run:

```bash

snakemake -j 1

Open the results/ folder — your .html should be there!

🧠 Tips & Troubleshooting

| Problem              | Fix                                          |
| -------------------- | -------------------------------------------- |
| “Missing input file” | Check path or file name                      |
| Nothing runs         | Did you specify `rule all` output correctly? |
| Rule runs every time | Output file name may not be exact            |
| Snakefile not found  | Make sure you’re in the right folder         |

📚 Learn More
Snakemake Docs (https://snakemake.readthedocs.io/)

Bioinformatics with Snakemake (YouTube) (https://youtu.be/hkGgW4EwRt8)

Workflow Examples (https://snakemake.github.io/snakemake-workflows/)

✅ Final Summary

| Task              | Command              |                       |
| ----------------- | -------------------- | --------------------- |
| Run pipeline      | `snakemake -j 1`     |                       |
| Dry run (preview) | `snakemake -np`      |                       |
| Visualize DAG     | \`snakemake --dag    | dot -Tpdf > dag.pdf\` |
| Unlock project    | `snakemake --unlock` |                       |







