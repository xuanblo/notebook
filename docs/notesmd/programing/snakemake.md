# Snakemake
>Summary: Snakemake is a workflow engine that provides a readable Python-based workflow definition language and a powerful execution environment that scales from single-core workstations to compute clusters without modifying the workflow. It is the first system to support the use of automatically inferred multiple named wildcards (or variables) in input and output filenames. Rules describe how to create output files from input files.

**Table of Contents**

- [Tutorials](#tutorials)  
- [Examples](#examples)

## Tutorials
- [Official manual v4.8.0](https://snakemake.readthedocs.io/en/stable/)
- [Paper](https://www.ncbi.nlm.nih.gov/pubmed/28096075)

## Examples

example 1: trimmomatic
```python

# trim by trimmomatic

import os

# input data
samples = {f[:-8] for f in os.listdir("clean_data") if f.endswith(".fq.gz")}

# some vars
cleanDir = "clean_data"
trimmedDir = "trimmed_data"
mappedDir = "mapped_data"
indexdir = "../../analysis/ref"

# this is target file
rule final:
    input: expand(trimmedDir + "/{sample}_1.paired.fq.gz", sample=samples)

rule paired_trimming:
    input:
        fwd= cleanDir + "/{sample}_1.fq.gz",
        rev= cleanDir + "/{sample}_2.fq.gz",
    output:
        fwd_paired= trimmedDir + "/{sample}_1.paired.fq.gz",
        fwd_unpaired= trimmedDir + "/{sample}_1.unpaired.fq.gz",
        rev_paired= trimmedDir + "/{sample}_2.paired.fq.gz",
        rev_unpaired= trimmedDir + "/{sample}_2.unpaired.fq.gz",
    message: """---start trimming.---"""
    threads: 4
    shell: """
        trimmomatic PE -threads {threads} {input.fwd} {input.rev} {output.fwd_paired} {output.fwd_unpaired} {output.rev_paired} {output.rev_unpaired} SLIDINGWINDOW:5:20 LEADING:20 TRAILING:20 MINLEN:50
    """
```
download this file and just run: `snakemake -np -s trimmomatic.Snakefile --cores 16` to see the jobs first.
or run: `snakemake -s trimmomatic.Snakefile` to get the result. you may also add `-F` to run fource.




 

