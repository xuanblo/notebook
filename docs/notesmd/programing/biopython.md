# Working with sequence

if you have a FASTA file `ls_orchid.fasta`
```
>gi|2765658|emb|Z78533.1|CIZ78533 C.irapeanum 5.8S rRNA gene and ITS1 and ITS2 DNA
CGTAACAAGGTTTCCGTAGGTGAACCTGCGGAAGGATCATTGATGAGACCGTGGAATAAACGATCGAGTG
AATCCGGAGGACCGGTGTACTCAGCTCACCGGGGGCATTGCTCCCGTGGTGACCCTGATTTGTTGTTGGG
...
```

## reading sequence file
```python

from Bio import SeqIO
for seq_record in SeqIO.parse("ls_orchid.fasta", "fasta"):
    print(seq_record.id)
    print(seq_record.name)
    print(seq_record.description)
    print(seq_record.features)
    print(repr(seq_record.seq)) #repr() 函数将对象转化为供解释器读取的形式。
    print(len(seq_record))
```


## SeqIO.parse return a iterator
```python
record_iterator = SeqIO.parse("ls_orchid.fasta", "fasta")
record = record_iterator.next()
```

## Getting a list of the records in a sequence file
```python
from Bio import SeqIO
records = list(SeqIO.parse("ls_orchid.gbk", "genbank"))

print("Found %i records".format(len(records))

print "The last record"
last_record = records[-1] #using Python's list tricks
```


## See also `SeqIO.read`:
```python
from Bio import SeqIO
record = SeqIO.read("ls_orchid.fasta", "fasta")
>>> record
SeqRecord(seq=Seq('CGTAACAAGGTTTCCGTAGGTGAACCTGCGGAAGGATCATTGATGAGACCGTGG...GGG', SingleLetterAlphabet()), id='gi|2765658|emb|Z78533.1|CIZ78533', name='gi|2765658|emb|Z78533.1|CIZ78533', description='gi|2765658|emb|Z78533.1|CIZ78533 C.irapeanum 5.8S rRNA gene and ITS1 and ITS2 DNA', dbxrefs=[])
>>> "GAATTC" in record
False
```

## Sequence files as Dictionaries - In memory
```python
from Bio import SeqIO
orchid_dict = SeqIO.to_dict(SeqIO.parse("ls_orchid.gbk", "genbank"))
print(orchid_dict.keys())
print(orchid_dict.values())
```

!!! info "Reasons to choose Bio.SeqIO.to_dict() over either Bio.SeqIO.index() or Bio.SeqIO.index_db() boil down to a need for flexibility despite its high memory needs."


## write
```python
SeqIO.write()
```