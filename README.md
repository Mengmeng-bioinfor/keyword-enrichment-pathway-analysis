# keyword-enrichment-pathway-analysis
A framework for performing keyword enrichment and biological pathway analysis based on gene sets, text mining, or functional annotations.
# Keyword Enrichment & Pathway Analysis

This repository provides a framework for performing enrichment analysis of keywords or biological terms in gene sets, and mapping them to known biological pathways.

## 🔍 Purpose

- Identify overrepresented biological processes, pathways, or terms in a gene or keyword list.
- Map significant keywords to KEGG, Reactome, or GO pathways.
- Visualize enriched terms and networks.

## 🚀 Features

- Term/gene set overrepresentation analysis (ORA)
- Support for KEGG, Reactome, GO annotations
- Custom text-based keyword enrichment (e.g., PubMed abstracts)
- Visualizations: bar plots, dot plots, enrichment maps

## 📁 Structure

- `data/`: Input gene lists, annotations, keyword files
- `scripts/`: Python scripts for enrichment and plotting
- `results/`: Output tables and statistics
- `figures/`: Final publication-quality plots
- `docs/`: Documentation and notes

## ⚙️ Setup

### Using pip

```bash
pip install -r requirements.txt

# 🔍 Understanding the Principle of Keyword Enrichment Analysis

**Keyword enrichment analysis** (also known as **functional enrichment analysis**) is a bioinformatics method used to identify biological themes, pathways, or categories that are statistically overrepresented in a list of genes (e.g., differentially expressed genes from an experiment).

---

## 🎯 Goal

To determine **whether a predefined set of genes** (e.g., involved in a biological process or pathway) is **enriched** (i.e., appears more frequently than expected by chance) in your list of input genes.

---

## 🧬 Input Requirements

- A list of **input genes** (e.g., top genes ranked by expression, mutation, or differential abundance)
- A **reference gene set database** (e.g., GO terms, KEGG pathways, Reactome, WikiPathways)
- An **annotation source** that maps genes to biological categories

---

## ⚙️ Core Steps in Enrichment Analysis

### Step 1: Gene Input Loading

The gene list is read from a `.txt` file. These genes represent the **foreground** set of interest.

### Step 2: Querying Databases via `gProfiler`

The input gene list is queried against biological databases to test for enrichment using the [g:Profiler](https://biit.cs.ut.ee/gprofiler/gost) API.

### Step 3: Statistical Testing

Each category is tested using a **hypergeometric test** (or similar), asking:

> What is the chance of observing this many genes in this term just by chance?

- **Raw P-values**
- **Adjusted P-values** (e.g., FDR)

### Step 4: Effect Size — Enrichment Ratio

```math
Enrichment Ratio = (Observed / Input Genes) / (Background / Total Background)
