# mypileup (CSE185 Project Demo)

This is a demonstration project for CSE185. It implements a subset of the the "pileup" method available through samtools. See the [samtools mpileup](http://www.htslib.org/doc/samtools-mpileup.html) page for more details.

# Install instructions

Installation requires the `pyfaidx` and `pysam` libraries to be installed. You can install these with `pip`:

```
pip install pyfaidx pysam
```

Once required libraries are installed, you can install `mypileup` with the following command:

```
python setup.py install
```

Note: if you do not have root access, you can run the commands above with additional options to install locally:
```
pip install --user pyfaidx pysam
python setup.py install --user
```

If the install was successful, typing `mypileup --help` should show a useful message.

# Basic usage

The basic usage of `mypileup` is:

```
mypileup [-f ref.fasta] [other options] in.bam
```

To run `mypileup` on a small test example (using files in this repo):
```
mypileup -f example-files/test.fa example-files/test.bam
```

This should produce the output below:
```
chrTEST	3	C	1	^!.	F
chrTEST	4	T	2	.^!.	FH
chrTEST	5	A	2	..	FH
chrTEST	6	G	2	..	FH
chrTEST	7	C	2	..	FH
chrTEST	8	T	2	..	FH
chrTEST	9	A	2	..	FH
chrTEST	10	C	2	.G	FH
chrTEST	11	G	2	..	FH
chrTEST	12	T	2	..	FH
chrTEST	13	A	1	T	H
```

To compare to output of `samtools mpileup`, run:
```
samtools mpileup --no-baq -f example-files/test.fa example-files/test.bam
```

# mypileup options

The only required input to `mypileup` is a (sorted, indexed) BAM file. Users may additionally specify the options below:

* `-f FILE`, `--fasta FILE`: faidx indexed reference sequence file. If specified, the mpileup format includes the reference base at each position (in column 3). Otherwise, the reference position at each base is listed as "N".

* `-r REG`, `--region REG`: region in which pileup is generated. Format chr:start-end. By default, the entire BAM file is processed.

* `-o FILE`, `--output FILE`: Write output to file. By default, output is written to stdout.


# File format

The output file format is the same as the samtools mpileup method. See: http://www.htslib.org/doc/samtools-mpileup.html


