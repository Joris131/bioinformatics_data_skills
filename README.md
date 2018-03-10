# bioinformatics_data_skills

Bioinformatics projects can involve mountains of code, and one of our best defenses
against bugs is to write code for humans, not for computers.

In bioinformatics work, it’s good to develop the habit of letting your computer do this sort of repetitive work for you

Our best approach to prevent this type of error(silent error) is to explicitly state and test our assumptions about data in our code using assert statements like Python’s assert() and R’s stopifnot()-Make Assertions and Be Loud, in Code and in Your Methods. In bioinformatics (and all fields), it’s crucial that we do as much as possible to turn the dreaded silent error into loud
errors.

A good practice to adopt is to document each of your analysis steps in plain-text
README files.

Better Writing scripts to produce images and tables

1. brace expansion(A type of shell expansion)

$ echo dog-{gone,bowl,bark}
dog-gone dog-bowl dog-bark

Using this same strategy, we can create the zmays-snps/ project directory:
$ mkdir -p zmays-snps/{data/seqs,scripts,analysis}

2. the Unix shell wildcard, the asterisk character ( * ):?

$ cd data
$ touch seqs/zmays{A,B,C}_R{1,2}.fastq
$ ls seqs/
zmaysA_R1.fastq zmaysB_R1.fastq zmaysC_R1.fastq
zmaysA_R2.fastq zmaysB_R2.fastq zmaysC_R2.fastq

$ ls seqs/zmaysB*
zmaysB_R1.fastq zmaysB_R2.fastq

#it’s best to be as restrictive as possible with wildcards to against accidental matches. So the command should be:
$ touch zmaysB*fastq or zmaysB_R?.fastq (the ? only matches a single
character)

3. Suppose a collaborator tells you that the C sample sequences are poor
quality, so you’ll have to work with just the A and B samples while C is resequenced.
You don’t want to delete zmaysC_R1.fastq and zmaysC_R2.fastq until the new samples
are received, so in the meantime you want to ignore these files. The folks that invented
wildcards foresaw problems like this, so they created shell wildcards that allow you to
match specific characters or ranges of characters. For example, we could match the
characters U, V, W, X, and Y with either [UVWXY] or [U-Y] (both are equivalent). Back
to our example, we could exclude the C sample using either:

$ ls zmays[AB]_R1.fastq
zmaysA_R1.fastq zmaysB_R1.fastq

$ ls zmays[A-B]_R1.fastq
zmaysA_R1.fastq zmaysB_R1.fastq

4. ls -lrt
Adding -lrt to the ls lists files in this directory in list format ( -l ), in reverse ( -r ) time
( -t ) order (see man ls for more details). If you wished to see the newest files at the top, you could
omit the r flag.

5. 创建文档时常以时间命名，这时候可以用 date +%F ，例如：

mkdir results-$(date +%F)
$ ls results-2015-04-13

6. Early Unix users were a clever (or lazy) bunch and devised a tool for storing repeated command
combinations: alias . If you’re running a clever one-liner over and over again, use add alias to add it to your ~/.bashrc (or ~/.profile if on OS X). alias simply aliases your command to a shorter name alias.
For example, if you always create project directories with the same directory structure, add a line like the following:

alias mkpr="mkdir -p {data/seqs,scripts,analysis}"

7. git的使用





