# R-based-Sequence-Analysis

## Project Overview
This project is divided into **two parts**:

**Part 1:** Gene expression analysis and tree growth study (10 questions).  
**Part 2:** Biological sequence diversity analysis comparing *Anaerococcus tetradius* and *E. coli* (6 questions).  

All analyses are implemented in **R**, with outputs saved in the `Output` folder for reproducibility.

---

## Repository Structure

Project/

├── Data/ # Input files

│ ├── Anaerococcus_tetradius.cds.all.fa.zip

│ ├── Escherichia_coli.cds.fa.zip

│ ├── gene_expression.tsv

│ └── growth_data.csv

├── Output/ # Outputs (CSV, PNGs)

│ ├── Part_1/

│ └── Part_2/

├── R script

└── README.md

---

## How to Run the Project

1. Install required packages:
```r
install.packages(c("seqinr", "R.utils", "dplyr", "ggplot2", "tidyr", "DESeq2"))
```

2. Create output directories:

```r
dir.create("Output/Part_1", recursive = TRUE)
dir.create("Output/Part_2", recursive = TRUE)
```

3. Run scripts sequentially:

```{r}
  source("R script.R")
```

4. Check Output folder for tables, CSVs, and plots.
---

# Part 1: Gene Expression and Tree Growth

### Q1–Q4: Gene Expression Summary
- **Q1:** Import gene expression data and preview the first 6 rows 
- **Q2:** Add a new column for mean expression across all samples 
- **Q3:** Identify the 10 genes with the highest mean expression 
- **Q4:** Count how many genes have a mean expression value less than 10

**Key Output:**
<img width="1420" height="232" alt="image" src="https://github.com/user-attachments/assets/c0a3d624-f958-4bfc-b116-bbe76151b51c" />

<img width="1774" height="237" alt="image" src="https://github.com/user-attachments/assets/53070851-efe9-4729-b6e2-ddb7084be5fd" />

<img width="1766" height="342" alt="image" src="https://github.com/user-attachments/assets/97a5fa5f-a3ab-44ce-9f4c-99f0efa2dbdc" />


### Q5–Q7: Normalization and Differential Expression
- **Q5:** Create a histogram of mean gene expression  
- **Q6:** Import tree growth data and check column names  
- **Q7:** Calculate mean and standard deviation of tree circumference at start (2005) and end (2020)

**Representative Output:**  

<img width="887" height="571" alt="image" src="https://github.com/user-attachments/assets/0f273dc0-0f71-4fe3-b495-45ed32424012" />

<img width="1754" height="244" alt="image" src="https://github.com/user-attachments/assets/8e926c18-0e43-4914-965a-c996e806d932" />

<img width="1779" height="153" alt="image" src="https://github.com/user-attachments/assets/26ec5b6a-795a-4d38-aa12-9fd349514f04" />



### Q8–Q10: Statistical Comparisons and Growth Analysis
- **Q8:** Analyzed tree growth per site using boxplots 
- **Q9:** Calculate mean growth over the last 10 years (2010–2020) by site  
- **Q10:** Conducted Welch Two-Sample t-tests

**Representative Output:**  

<img width="826" height="509" alt="image" src="https://github.com/user-attachments/assets/ca8c44c8-b105-4745-bc90-9eb8971ca17e" />

<img width="453" height="140" alt="image" src="https://github.com/user-attachments/assets/8537d0c3-2f94-46a5-a6f3-d74d4bc70f71" />

<img width="772" height="251" alt="image" src="https://github.com/user-attachments/assets/3c801724-22ed-443a-b267-92fc5e58faf7" />

---

# Part 2: Biological Sequence Diversity

### Q1: Number of Coding Sequences
- Counted CDS for both organisms using `seqinr`.
  
- **Output Table:**
  
| Organism | Number_of_CDS |
|----------|---------------|
| Anaerococcus tetradius | 1836 |
| Escherichia coli       | 4239 |

---

### Q2: Total Coding DNA
- Summed all CDS lengths for each organism.
  
- **Output Table:**
  
| Organism | Total_Coding_DNA_bp |
|----------|-------------------|
| Anaerococcus tetradius | 1,758,063 |
| Escherichia coli       | 3,978,528 |

---

### Q3: CDS Length Distribution
- Calculated mean and median CDS lengths.  
- Visualized with a boxplot.
  
**Representative Plot:**
  
<img width="839" height="520" alt="image" src="https://github.com/user-attachments/assets/c51377ac-6c1d-4d95-ba35-d1bd9f457beb" />


| Organism | Mean_CDS_Length | Median_CDS_Length |
|----------|----------------|-----------------|
| Anaerococcus tetradius | 957.55 | 804 |
| Escherichia coli       | 938.55 | 831 |

---

### Q4: Nucleotide and Amino Acid Frequencies
- Calculated nucleotide frequencies and amino acid composition.
  
- **Observations:**  
  - *E. coli* has higher GC-content.  
  - Amino acid profiles differ significantly between organisms.  

**Representative Plots:**  
- Nucleotide frequency: `Output/Part_2/Nucleotide_Frequency.png`  
- Amino acid frequency: `Output/Part_2/AminoAcid_Frequency.png`

<img width="826" height="512" alt="image" src="https://github.com/user-attachments/assets/4229fcf8-3755-473a-9276-7eb7e6937442" />

<img width="826" height="509" alt="image" src="https://github.com/user-attachments/assets/9433261c-7a0c-4b73-9673-de3062a4d170" />


---

### Q5: Codon Usage Bias
- Created codon usage tables and calculated relative frequencies.  
- **Observations:** Codon usage reflects underlying genomic GC/AT content.  

**Representative Plot:**  
- Codon usage chart: `Output/Part_2/Codon_Usage.png`  

<img width="822" height="521" alt="image" src="https://github.com/user-attachments/assets/24828fd6-413f-42b4-91a6-0fff8aaa727e" />

---

### Q6: Protein k-mer Analysis
- Counted k-mers of length 3–5 in *Anaerococcus* proteins.  
- Identified top 10 overrepresented and underrepresented k-mers.  
- Compared frequencies with *E. coli*.  

**Outputs (CSV files):**
- `Anaerococcus_k3_top10_over.csv`, `Anaerococcus_k3_bottom10_under.csv`  
- `Anaerococcus_k4_top10_over.csv`, `Anaerococcus_k4_bottom10_under.csv`  
- `Anaerococcus_k5_top10_over.csv`, `Anaerococcus_k5_bottom10_under.csv`  

**Representative Plots:**  
- Top 3-mer overrepresented: `Output/Part_2/Anaerococcus_k3_Top10_Over.png`  
- Bottom 3-mer underrepresented: `Output/Part_2/Anaerococcus_k3_Bottom10_Under.png`

<img width="833" height="516" alt="image" src="https://github.com/user-attachments/assets/574eb41e-8a69-4258-bd8c-afd856bb07d9" />

<img width="821" height="513" alt="image" src="https://github.com/user-attachments/assets/7837fb53-5189-4c31-b929-c0f56c5518ce" />
 
**Observation:**  
- Overrepresented k-mers are linked to functional/structural features or codon bias.  
- Underrepresented k-mers may be avoided for translational or structural reasons.

---

-- **End** --


