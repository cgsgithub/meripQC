# meripQC
Benchmarking for MeRIP-seq data analysis

hoper
===
<p align="justify">It is a python package used to Benchmark the MeRIP-seq data.</p>

Installation
------------

* Get the current repo
```
wget https://github.com/luolab/hoper/archive/hoper_1.0.0.zip
```

* Install the python3 and dependent python packages
- python3
- scipy
- numpy
- pandas
- matplotlib
- seaborn
- requests
- statsmodels

The python3 and all the dependent python packages above are included in anaconda3. So 
we strongly recommend the installation of anaconda3.



* Download the anaconda3

If you are in China, please use this command:

```
wget https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/Anaconda3-5.2.0-Linux-x86.sh
```

If you are not in China, use this command:

```
wget https://repo.anaconda.com/archive/Anaconda3-5.2.0-Linux-x86.sh
```


* Install anaconda3

```
bash Anaconda3-5.2.0-Linux-x86.sh -p write-permission-directory/anaconda3
```

* Add anaconda3 to environment variable

```
export PATH=complete_path_to_anaconda3/bin:$PATH
```

* Check it

```
which python
```
If successful, it will return similar result
```
/public/work/guoshi/bin/anaconda3/bin/python
```
* Install other dependent tools
- samtools
- bedtools
- weblogo

If samtools, bedtools, weblogo are not installed in your linux system, installing them by conda is Recommended.
First, add the bioconda channel as well as the other channels bioconda depends on:

```
conda config --add channels defaults
conda config --add channels conda-forge
conda config --add channels bioconda
```

Second, run the install command:
```
conda install samtools
conda install bedtools
conda install weblogo
```

* Download and unzip the hoper code

```
tar zxvf hoper.tar.gz
cd hoper
```

* Then install hoper

```
pip install .
```

* Check the installation

```
hoper -h
```

Usage
-----

List all the options
 
```
hoper -h
```



Run hoper using 2 sample replicates to test:

* Single end Test Samples information

| Replicates | Sample | Type |
| :---- | :---- | :---- |
| rep1 | W6_S27_chr20.bam | IP |
| rep1 | W2_S22_chr20.bam | INPUT|
| rep2 | W8_S24_chr20.bam | IP |
| rep2 | W4_S23_chr20.bam | INPUT |


* Paired end Test Samples information


| Replicates | Sample | Type |
| :---- | :---- | :---- |
| rep1 | SRR1182603_chr20.bam | IP |
| rep1 | SRR1182604_chr20.bam | INPUT|
| rep2 | SRR1182605_chr20.bam | IP |
| rep2 | SRR1182606_chr20.bam | INPUT |


* Single end sequencing
```
hoper -p W6_S27_chr20.bam,W8_S24_chr20.bam -u W2_S22_chr20.bam,W4_S23_chr20.bam -t SE -s hg19 -g genes_chr20.gtf -r 50 -o hoper_test_SE
```

* Paired end sequencing
```
hoper -p SRR1182603_chr20.bam,SRR1182605_chr20.bam -u SRR1182604_chr20.bam,SRR1182606_chr20.bam -t PE -s hg19 -g genes_chr20.gtf -r 30 -o hoper_test_PE
```

If you have 3 sample Replicates, use comma to separate sample replicates. Note: There is no space between commas.
