# ML Review Paper — High-Dimensional, Small-Sample Data

This is a group coursework paper me and two teammates wrote for the Machine Learning 01 module (Coursework 02) in our HND in Data Science at NIBM.

The task was to pick a research paper and write a review of it. We picked this one:

> Pirooznia, M., Yang, J. Y., Yang, M. Q., & Deng, Y. (2008). A comparative study of different machine learning methods on microarray gene expression data. *BMC Genomics*, 9(Suppl 1), S13.

It's about a common problem in data science: what happens when you have way more features (columns) than samples (rows), like a gene dataset with 8,000 genes but only 30 patients. The paper compares different ML models (SVM, decision trees, random forest, neural nets, etc.) and feature selection methods on that kind of data.

Our review looks at what that paper found, where it falls a bit short (small sample sizes, no confidence intervals, and so on), and how newer research from 2022–2023 has tried to fix those gaps.

## Team

- P. U. O. Fernando (HNDDS25.2-002)
- P. S. S. Vithanage (HNDDS25.2-003)
- D. M. D. Gunawardhana (HNDDS25.2-004)

**Module:** Machine Learning 01 — Coursework 02
**Institute:** National Institute of Business Management (NIBM), HND in Data Science, Batch HNDDS 25.2F
**Date:** August 2026

## Files

- `ML_Review_Paper` — the full paper, readable directly on GitHub
- `ML_Review_Paper` — the same paper as a formatted PDF (title page, page numbers, exactly as we printed and submitted it)

## What's inside

- How the original study set up its comparison (8 microarray datasets, 7 classifiers, 3 feature selection methods)
- Which models did best without any feature selection
- Why feature selection made such a big difference on this kind of data
- Where the study's methodology has weak points
- What later papers (2022–2023) did differently to handle high-dimensional, small-sample data
