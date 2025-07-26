# 🧪 FastQC – Quality Control for FASTQ Files

**FastQC** is a simple but powerful tool that helps you evaluate the quality of your raw sequencing data.  
It works with `.fastq` or `.fastq.gz` files and provides detailed visual reports on common issues like:

- Poor quality scores
- Adapter contamination
- Overrepresented sequences
- GC content anomalies

Before using any read aligners (like `BWA`, `STAR`, or `HISAT2`), you should always run FastQC.

---

## 🧾 What This Page Covers

- 📦 How to install FastQC
- 📁 What input files it needs
- 🚀 How to run it
- 📊 How to interpret the results
- 🧠 Tips and troubleshooting
- 📚 Resources and practice examples

---

## 📦 Installation

### ✅ Best Option: Using Conda (Recommended)

```bash
conda install -c bioconda fastqc

🧪 Check Installation
```bash
fastqc --help

You should see usage instructions.

📁 Input File Format
FastQC works with:

reads.fastq

reads.fastq.gz (compressed)

📌 You can use both single-end and paired-end read files.

🚀 Running FastQC
▶️ Basic Usage
```bash
fastqc reads.fastq

or for compressed files:
```bash
fastqc reads.fastq.gz

📦 Batch Processing
```bash
fastqc *.fastq.gz

🔁 This will create .html and .zip files for each input FASTQ file.

📁 Output Files
| File                | Description                                  |
| ------------------- | -------------------------------------------- |
| `reads_fastqc.html` | Interactive quality report (open in browser) |
| `reads_fastqc.zip`  | Compressed version of the data tables        |

The html file is what you’ll look at for results.

📊 How to Read the Report
🟢 FastQC Modules Summary:


| Module                        | What it checks                       | Tip                                   |
| ----------------------------- | ------------------------------------ | ------------------------------------- |
| **Per base sequence quality** | Quality scores at each base position | ✅ Should be mostly green              |
| **Per sequence GC content**   | Expected GC distribution             | ⚠️ Species-specific                   |
| **Adapter Content**           | Contamination from library adapters  | ❌ Remove with Trimmomatic or Cutadapt |
| **Overrepresented sequences** | Duplicated or contaminant reads      | Investigate the sequence              |
| **Per base N content**        | Proportion of unknown (N) bases      | Should be near 0                      |

🧠 Click each module in the HTML report to see graphs and explanations.

🧠 Tips & Best Practices

| Tip                                          | Why                                     |
| -------------------------------------------- | --------------------------------------- |
| Run FastQC **before and after** trimming     | To confirm QC improvement               |
| Use `multiqc` to combine many FastQC reports | Especially useful for dozens of samples |
| Store `.zip` files for future reference      | Some tools read FastQC data             |
| Use `--threads N` to speed up processing     | FastQC is multi-threaded                |

▶️ Example with threads and output directory:
```bash

fastqc *.fastq.gz --threads 4 --outdir qc_reports/

🧪 Sample Practice Dataset
You can download a tiny test FASTQ file:

```bash

wget https://raw.githubusercontent.com/lh3/readfq/master/test.fq
fastqc test.fq

Then open the test_fastqc.html in your browser.

🧰 Common Errors & Fixes

| Error                | Solution                                                              |
| -------------------- | --------------------------------------------------------------------- |
| `command not found`  | Reinstall FastQC via conda                                            |
| Java-related errors  | Make sure `java` is installed: `conda install -c conda-forge openjdk` |
| `.html` doesn't open | Use: `firefox file.html` or move to a GUI system                      |


📚 Learn More
🔗 FastQC Homepage (https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)

🐍 Install with Bioconda (https://bioconda.github.io/recipes/fastqc/README.html)

📖 Understanding FastQC Modules (https://hbctraining.github.io/Intro-to-rnaseq-hpc-O2/lessons/02_fastqc.html)

✅ Summary

| Step                   | Command                                              |
| ---------------------- | ---------------------------------------------------- |
| Run FastQC on 1 file   | `fastqc sample.fastq.gz`                             |
| Run on all files       | `fastqc *.fastq.gz`                                  |
| Save reports elsewhere | `fastqc *.fastq.gz --outdir qc_reports/`             |
| Open report            | Double-click `.html` or `firefox sample_fastqc.html` |






