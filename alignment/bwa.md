# 🧬 BWA – Burrows-Wheeler Aligner

BWA is a fast and widely used tool for **aligning short DNA reads** (e.g., from Illumina sequencing) to a reference genome. It is one of the most basic and important tools in a typical DNA-seq pipeline.



## 🧾 What Is Alignment?

Alignment is the process of **mapping sequencing reads** (from a `.fastq` file) to a reference genome (`.fasta` file). This helps us know **where in the genome each read comes from** — a critical step before variant calling, expression analysis, or genome assembly.



## 📦 Installation

### ✅ Using Conda (Recommended)

If you use conda (like with Miniconda or Mamba):

```bash
conda install -c bioconda bwa


🧪 Check Installation
```bash
bwa
You should see a help menu. If not, the install failed.

📁 Required Input Files

| File     | Description      | Example                            |
| -------- | ---------------- | ---------------------------------- |
| `.fasta` | Reference genome | `genome.fasta`                     |
| `.fastq` | Sequencing reads | `reads_R1.fastq`, `reads_R2.fastq` |

📑 Step-by-Step Workflow
✅ Step 1: Index the Reference Genome:
```bash
bwa index genome.fasta

✅ Step 2: Align Reads to the Reference
🧬 For Paired-End Reads:
```bash
bwa mem genome.fasta reads_R1.fastq reads_R2.fastq > aln.sam

🧬 For Single-End Reads:
```bash
bwa mem genome.fasta reads.fastq > aln.sam

📤 Output: aln.sam — a plain-text file with alignment results

✅ Step 3: Convert SAM → BAM → Sort → Index
We use samtools for post-processing.
```bash
# Convert SAM to BAM
samtools view -Sb aln.sam > aln.bam

# Sort the BAM file
samtools sort aln.bam -o aln.sorted.bam

# Index the sorted BAM
samtools index aln.sorted.bam

📦 BAM = Binary version of SAM (faster, smaller)
📁 BAM index = Needed for tools like IGV and variant calling


📷 Workflow Summary Diagram (Text Version)
 FASTQ reads
     ↓
  BWA MEM
     ↓
   SAM file
     ↓
 samtools view
     ↓
   BAM file
     ↓
 samtools sort + index
     ↓
Sorted + indexed BAM (ready for downstream)

🧠 Practical Tips

| Tip                | Why                                             |
| ------------------ | ----------------------------------------------- |
| Use `-t N`         | Run with `N` threads (faster): `bwa mem -t 4`   |
| Use `gzip` files   | BWA can read `.fastq.gz` directly               |
| Paired-end reads   | Always match read order (R1 + R2)               |
| Quality trimming   | Always run `fastqc` + trimming before alignment |
| Use absolute paths | To avoid file not found errors                  |

🛠️ Common Errors & Fixes

| Error                  | Solution                               |
| ---------------------- | -------------------------------------- |
| `fail to open file`    | Check file paths and extensions        |
| `segmentation fault`   | Reinstall BWA or use smaller dataset   |
| SAM has 0 alignments   | Wrong reference file or trimming error |
| BWA runs but no `.bam` | You must redirect output using `>`     |

🧪 Test Dataset (Try This!)
You can try BWA using a tiny reference and fake reads:
```bash
wget https://raw.githubusercontent.com/jake-andrews/bwa-mini-example/main/genome.fasta
wget https://raw.githubusercontent.com/jake-andrews/bwa-mini-example/main/reads.fastq

bwa index genome.fasta
bwa mem genome.fasta reads.fastq > aln.sam

📚 Learn More
📘 BWA GitHub (https://github.com/lh3/bwa)

📄 Original Paper (https://academic.oup.com/bioinformatics/article/25/14/1754/225615)

📘 SAM/BAM Format Explained (https://samtools.github.io/hts-specs/SAMv1.pdf)

✅ Final Summary

| Step           | Command                                      |
| -------------- | -------------------------------------------- |
| Index genome   | `bwa index genome.fasta`                     |
| Align reads    | `bwa mem genome.fasta R1.fq R2.fq > aln.sam` |
| Convert to BAM | `samtools view -Sb aln.sam > aln.bam`        |
| Sort BAM       | `samtools sort aln.bam -o aln.sorted.bam`    |
| Index BAM      | `samtools index aln.sorted.bam`              |

👨‍🔬 This guide is beginner-friendly, clean, and reproducible — perfect for bioinformatics learners.
Save it. Practice it. And when you're ready, we’ll move on to fastqc.md.


## ✅ What To Do Now

1. Go to your GitHub repo → `alignment/`
2. Click **“Add file” → “Create new file”**
3. Name the file: `bwa.md`
4. Paste the entire content above
5. Click **“Commit new file”**




