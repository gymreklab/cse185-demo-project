# Benchmarking mypileup against samtools mpileup

## Timing

```
time mypileup -f ../example-files/test.fa ../example-files/test.bam

time samtools mpileup --no-baq -f ../example-files/test.fa ../example-files/test.bam
```

## Memory usage

See: https://github.com/jhclark/memusg
Note, this command was failing on OSX but worked on Ubuntu

```
memusg mypileup -f ../example-files/test.fa ../example-files/test.bam

memusg samtools mpileup --no-baq -f ../example-files/test.fa ../example-files/test.bam
```
