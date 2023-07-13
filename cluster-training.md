### Cluster training

## Q1

There are `.` and `..`. Those indicate the current directory and parent directory respectively.

## Q2

`cat` shows all contents at once but `more` and `less`  shows the contents one screen at a time. `less` has both forward and barckward navigation option and it can be navigated by the arrow key. `less` seems more usefuls than `cat` and `more`. 

## Q3

`wc -l HN002_training_jyhan.vcf` command indicates there are 200 lines in this file.

## Q4

The compression ration of `gzip` is around 68% (from 29945 to 9648) and `bzip2` is around 71% (from 29945 to 8567). `bzip2` has a higher compression ratio, so I recommand to use `bzip2`.

## Q5

`more` can't show the file contents, but `less` can display the file contents.

## Q6

A softlink can link to a file or directory instead of copying them, so it can save the disk space. But, if the priginal file is moved, deleted or renamed, the link will not work anymore.

## Q7

There are total 3366 sequence reads and 2841 read are with `chr`. There are 25 chromosomes chr1 - 22, X, Y and M.

## Q8

```
docker run --rm -u $(id -u):$(id -g) \
    -v $(pwd):$(pwd) -w $(pwd) \
    -v /hot/cluster-training:/hot/cluster-training \
    ghcr.io/uclahs-cds/samtools:1.15.1 \
    samtools faidx Homo_sapiens_assembly38.fasta
```

`docker run`: to run a Docker container.
`--rm`: Docker is automatically removed when it exits.
`-u $(id -u):$(id -g)`: avoid run Docker as root (The root user have all permission to manage all files). The user and group id are set. 
`-v`: to mount the current working directory
`-w`: to set the working directory inside the container to the current working directory.
`-v /hot/cluster-training:/hot/cluster-training`: to mount the directory to the same path inside the container to enabel the container to access files located in the directory.
`ghcr.io/uclahs-cds/samtools:1.15.1`: to use samtools command
`samtools faidx Homo_sapiens_assembly38.fasta`: command generating .fai file

## Q9

The two files are not identical. I can use `cat` for visual inspection and also use `diff` to compare two files. The output, `1c1`, indicates the 1st line of both files are different.

## Q10

This error happens when Docker doesn't recognize a user or group ID since Docker create the separate environment from cluster.

# Q11

2 cpus

# Q12

3.7 GB

# Q13

around 1:2

# Q14

F2-42/F16-5/F32-10/F72-25/M64-1

# Q15

`srun --partition=F16 -c 2 --mem=4G --pty bash`

# Q16

126 hrs: total used hours
126 * 0.34 (compute) + 126 * 0.08 (scratch SSD) = $52.92

# Q17

40 hrs * 1.5 (compute) + 40 hrs * 0.3 = $72

# Q18

The command show that the usage is 3.2 PB. Including 50% for snapshots, the total cost is
3.2 PB * 1.5 (including snapshots) * 0.000027 * 24 (hour) * 30 (day) * 1000000 (PB to GB) = $93,312

The way to reduce the cost is trying not to store the data in /hot. We can delete the data which don't need anymore or compress the files.

# Q19

`/hot/users/permission-test`: I can only access to trainee folder which mean I have only boutrostrainee permission. `drwxrws---` mean the people in indicated group can read and write to that directory.
I can see I'm involved in boutrostrainee from `/etc/group`

# Q20

When type `which R`, it shows there is no R in current directory.
After typing `module load R` and `which R`, it loaded /mnt/moduleshare/moduleapps/R/4.2.1/bin/R.
The commands, `module load R/3.6.0` and `which R`, loaded the specific R version `/mnt/moduleshare/moduleapps/R/3.6.0/bin/R`.

# Q21

`module list` can show the list of all loaded modules.
`module purge` can unload all loaded modules.

# Q22

There are a total 305 installed packages.

There are 9 packages containing 'BoutrosLab'.
 "BoutrosLab.datasets.breast.cancer"
 "BoutrosLab.package.utilities"
 "BoutrosLab.plotting.general"
 "BoutrosLab.prognosticsignature.general"
 "BoutrosLab.statistics.classification"
 "BoutrosLab.statistics.general"
 "BoutrosLab.statistics.survival"
 "BoutrosLab.utilities"
 "BoutrosLab.utilities.copynumber"







