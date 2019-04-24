# [
# NCBI-Hackathons
](https://github.com/NCBI-Hackathons)
# /
[
# TheHumanPangenome
](https://github.com/NCBI-Hackathons/TheHumanPangenome)
#

## [**TheHumanPangenome**](https://github.com/NCBI-Hackathons/TheHumanPangenome/tree/baa869cb42dd05fc0b18cae5728e35a0b87de9ff) **/** [**cloud-info**](https://github.com/NCBI-Hackathons/TheHumanPangenome/tree/baa869cb42dd05fc0b18cae5728e35a0b87de9ff/cloud-info) **/cloud-cheat-sheet.md**

#
# Tech Cookbook / Cheat-Sheet:

## **General Hackathon Info**

1. 1. **Connect to Slack**

First things first, you&#39;ll want to connect to the Slack space for the hackathon. The invitation link will be sent to your email that you used to register for your hackathon participationor feel free to contact NCBI hackathon leader or administrator for help. For the fastest and best support on the information in this document, Slack is your best bet. Look for a #help-desk channel once you have connected.

1. Create a github account

Go to [https://github.com](https://github.com) and select create an account.  Use an email that you can access remotely.

1. 3. **Create an ssh key which you will need to connect to all the things.**

#### **(what is this and why do I need to know this?)**

An ssh key is used to connect to github and to access servers. There are different ways to do that; this document outlines how to use a command line for these tasks.

Depending on your operating system of choice, you may already have a command line (terminal) and ssh-related tools installed (Mac, most Linux versions, newer Windows versions[10 or later]).

If not, you can install Git software from which will install a Git Bash program which when you run will provide a command line prompt for Windows

- [https://git-scm.com/downloads](https://git-scm.com/downloads)

(This will install on Windows machines fine even without administrator access.)

Once you have git installed (it&#39;ll appear as &#39;git bash&#39;), run it to open a command window. On a mac, open &quot;terminal&quot;. On linux, open a bash shell or your shell of choice. On Windows, left click the Windows symbol on the bottom left of your screen, then type in cmd in the &quot;search programs and files&quot; box and press the enter key.

### **Steps to create your public keys**

- If you want to know more about keys,  read  [Generating a new SSH Key for Github](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/), or follow the steps below.

1. Open the terminal or command line as described above
2. Paste the text below, substituting in your GitHub email address.

$ ssh-keygen -t rsa -b 4096 -C [your\_email@example.com](mailto:your_email@example.com)

do the cut and from the ssh…onwards, do not cut and paste the &quot;$ &quot;

This creates a new ssh key, using the provided email as a label (-C = comment).

Note: For github keys, it&#39;s customary to use the same email as your github account. For shell access, any string will do in the comment, with something@something-else. The something before the @ will be your username for connecting to cloud servers.

1. When you&#39;re prompted to &quot;Enter a file in which to save the key,&quot; press Enter. This accepts the default file location.

Enter a file in which to save the key (/home/you/.ssh/id\_rsa): [Press enter]

Optional: if you already have existing keys, you may want to give this key r a specific name.

1. At the prompt, type a secure passphrase. Note: - a pass phrase is not required

Enter passphrase (empty for no passphrase): [Type a passphrase]

Enter same passphrase again: [Type passphrase again]

You&#39;ll see a message indicating your key has been saved, with a default public key name of id\_rsa.pub in your .ssh folder.

### **Adding Keys to Github and Gaining Server Access**

Now that you have created an ssh key, you need to tell Github about it and provide it to the server / cloud admins so they can grant you access. Here&#39;s how to do that.

1. Log into Github
2. Click your avatar in the top right corner of the screen, and choose &quot;settings&quot; from the menu.
3. On the left side, click &quot;SSH and GPG Keys&quot;. You may be prompted for your password if you&#39;ve been logged in for a while.
4. Click the green &quot;New SSH Key&quot; button at the top of the screen.
5. Locate the id\_rsa.pub file you created previously (or any other custom-named public key). Copy the entire contents of the file and paste it into the &quot;Key&quot; box. Enter any string in the &quot;Title&quot; box as a name/label, and click &quot;Add SSH Key&quot; to save. (with Windows open with notepad – do not double click, do a single left click)
6. For write access to the hackathon repository, you need to provide your github username to the github admin - to do that, send a message in the #github\_usernames channel in Slack.
7. Once you are added, you&#39;ll get an invitation email. Open it, click the green button, and accept the invitation.
8. Finally, open the github repository page, and click the &quot;clone or download&quot; button. Copy the ssh github url (it&#39;ll look like git@github.com:NCBI-Hackathons/TheHumanPangenome.git), open a command prompt, and try the following command:

git clone git@github.com:NCBI-Hackathons/TheHumanPangenome.git

Enter your ssh key passphrase if prompted. If the repo is cloned - success!

#### **Server Access**

To get cloud server access, you need to provide your ssh public key to the server admin. To do that:

1. Copy the contents of your id\_rsa.pub file to a new message in the #public-keys slack channel.
2. Once your key is added, a friendly NCBI cloud admin will reply in Slack with a test command you can use to verify server access. It&#39;ll be something like: ssh yourusername@1.2.3.4 whoami
3. Run that commnd in a terminal; it should respond with your username.

- Server IP information is listed in the #help-desk channel in slack (pinned message).
- If you have trouble connecting, check the username, and try first with a simple command-line ssh client.

### **Markdown, for writing and formatting ReadMe and other documents on GitHub (like this document!)**

- [Markdown Help](https://commonmark.org/help/)
- [Handy Markdown cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

## **Where&#39;s the Data?!**

| **Data** | **Location** |
| --- | --- |
| SRA alignments | gs://ncbi\_sra\_rnaseq/\*.bam |
| Counts | gs://ncbi\_sra\_rnaseq/genecounts/\*.genecounts |
| Contig FASTAs | gs://ncbi\_sra\_rnaseq/\*.contigs.fa/ |
| BigQuery Tables | project: strides-sra-hackathon-data
table: rnaseq.genescounts, rnaseq.runinfo
project: strides-sra-hackathon-data
table: various, see 4a TODO: [below](https://github.com/NCBI-Hackathons/TheHumanPangenome/blob/baa869cb42dd05fc0b18cae5728e35a0b87de9ff/cloud-info/cloud-cheat-sheet.md) |
| Server information | Refer to the pinned post Slack (#help-desk channel) |
| Additional Tools | gs://ncbi\_hackathon\_aux\_tools/ |

## **How the data was generated**

We start with SRA run data pulled from NCBI and align it with hisat2 onto gs://ncbi\_sra\_rnaseq/refs/GCA\_000001405.15\_GRCh38\_no\_alt\_plus\_hs38d1\_analysis\_set.\*.ht2 Unmapped reads then are assembled using skesa into denovo contigs and aligned with hisat2 onto the contigs. The merged BAM file is stored on the bucket. BAM files are sorted and indexed, for each BAM there is a flagstat and counts files. The counts are also stored in the BigQuery table rnaseq.genescounts.

## **General GCP Advice**

### **Working with Google Storage (aka**  **gs**** ) buckets:**

- gsutil is a collection of command line tools to access and modify data stored in google storage buckets. [gsutil](https://cloud.google.com/storage/docs/gsutil)[Documentation Link](https://cloud.google.com/storage/docs/gsutil)
- gsutil Examples:
  - List files:

gsutil ls -l

gs://ncbi\_sra\_rnaseq/DRR016694\*.bam

-
  - Copy a file from the bucket to the current directory:

gsutil cp gs://ncbi\_sra\_rnaseq/DRR016694.bam .

-
  - Stream a file:

gsutil cat gs://ncbi\_sra\_rnaseq/DRR016694.flagstat | less

-
  - Copy multiple files from the bucket:

gsutil -m cp gs://ncbi\_sra\_rnaseq/DRR01669\*.bam .

Tip: To copy data between servers,

- use gsutil to copy from the source server to google storage first, then copy to the destination.
- r, add your ssh keys to the source server and use scp localfile username@REMOTE-IP:/foo/bar/

### **Google compute cloud tools (gcloud):**

- Check your service account and project: gcloud info
- Pub/sub queue:
  - Create a topic: gcloud pubsub topics create test1
  - Create a subscription to the topic: gcloud pubsub subscriptions create --topic test1 sub1
  - Publish a message to the topic: gcloud pubsub topics publish test1 --message qwe
  - Pull a message from the subscription: gcloud pubsub subscriptions pull sub1

### **BigQuery (a.k.a bq)**

- [https://cloud.google.com/bigquery/docs/bq-command-line-tool](https://cloud.google.com/bigquery/docs/bq-command-line-tool)

For reference use only -- _should not_ be included in an external docker

- Search data pre-indexed by NCBI
  - _Query format_: bq --project\_id strides-sra-hackathon-data query --nouse\_legacy\_sql

In some case you may need to use strides-sra-hackathon-data, more on this below

- _Useful options_:
- bq --max\_rows=100
-    --format=pretty
-    --project\_id strides-sra-hackathon-data query
-    --nouse\_legacy\_sql &quot;\&lt;your\_standard\_sql\_query\_here&quot;
-    ```
-

The format flag also takes &quot;json&quot; and &quot;csv&quot; as valid arguments

- _Available data_: bq show --schema --format=prettyjson strides-sra-hackathon-data:rnaseq.runinfo

Format also accepts &quot;json&quot;

## **Premade servers**

Several servers are available.

- See the pinned post in the #help-desk channel in slack for server IP addresses. Contact a friendly admin for access or to request a new or modified (more CPU, memory, disk) server.

## **Working with NCBI Data/Tools in the cloud**

### **SRA Realign Object Data and Contigs**

Realigned metagenomic SRA runs are located in the ncbi\_sra\_realign bucket. To access them directly please refer to gsutil.

The bucket with realigned runs should be mounted on the VMs during the main hackathon event under the directory /data/realign/. Realign files are named based on their corresponding SRA run accession number, for example /data/realign/SRR1158703.realign

Realign objects are effectively the same reads (bases) as the original SRA runs but aligned onto host (human) and either viral contigs or references and onto denovo contigs assembled with skesa.

- For example, realign contains 964 reads mapped onto human, 9043281 reads mapped onto denovo contigs and 1392735 unmapped reads:
- bq --maxrows=10000 --projectid strides-sra-hackathon-data
- query &#39;select \* from ncbisrarealign.summary where accession=&quot;SRR649927&quot;&#39;
- To check taxonomy of the contigs:
- bq --projectid strides-sra-hackathon-data
- query &#39;select \* from ncbisrarealign.taxonomy where accession=&quot;SRR649927&quot;&#39;`
- To extract contigs from a realign object:
- dump-ref-fasta --localref SRR649927.realign \&gt; SRR649927.contigs.fa
- Human references GRCh38.p12 was used to align reads before assembling the rest. Please find the full list of sequences here: [https://www.ncbi.nlm.nih.gov/assembly?term=GRCh38&amp;cmd=DetailsSearch](https://www.ncbi.nlm.nih.gov/assembly?term=GRCh38&amp;cmd=DetailsSearch)
- There are 2 types of contigs in realign objects: guided and denovo. Guided contigs have been built with guided assembler using a predefined viral reference set. These are almost 300 sequences including multiple Influenza serotypes, Herpes, Ebola etc.

The names of guided contigscan be filtered based on regex:

grep -P &#39;^(?\!Contig)\[A-Z0-9.\]+\_\\d+$&#39;

Contig names are based on reference sequence accession used as a guide. For example contig named KF021598.1\_1 has been built using KF021598.1 as a guide reference.

Denovo contigs have been assembled with skesa after filtering out human and viral reads. Their names start with Contig prefix.

Contig names are unique only within a realign object, not across realign objects.

### **SRA Toolkit**

(Already installed on pre-built hackathon VM instances)

Download from [https://www.ncbi.nlm.nih.gov/sra/docs/toolkitsoft/](https://www.ncbi.nlm.nih.gov/sra/docs/toolkitsoft/)

Or, copy the pre-release version from google storage:

gsutil cp gs://ncbi\_hackathon\_aux\_tools/sratoolkit.2.9.4.pre.tar.gz .

- Examples:
  - Lookup by accession: srapath \&lt;accession\&gt;
  - Download and cache run locally: prefetch \&lt;accession\&gt;
  - Get statistics: sra-stat --quick --xml \&lt;accession\&gt;
  - Dump reads into separate fastq files: fastq-dump --split-files --split-spot \&lt;accession\&gt;
  - Extract contigs (local sequences): dump-ref-fasta -l \&lt;accession\&gt;
  - Convert an SRA object to BAM: sam-dump --unaligned \&lt;accession\&gt; | samtools view -Sb -\&lt;accession\&gt;.bam

### **BLAST suite**

Instructions on running the dockerized BLAST are at [https://github.com/ncbi/docker/blob/master/blast/README.md](https://github.com/ncbi/docker/blob/master/blast/README.md)

Make sure the BLAST\_DIR env variable is set before you try the commands.

For a complete list of command-line blast arguments see: [https://www.ncbi.nlm.nih.gov/books/NBK279684/#](https://www.ncbi.nlm.nih.gov/books/NBK279684/#_appendices_Options_for_the_commandline_a_)[_appendices\_Options\_for\_the\_commandline\_a_](https://www.ncbi.nlm.nih.gov/books/NBK279684/#_appendices_Options_for_the_commandline_a_)

BLAST has a lot of flexibility in how it presents results:

- Use the -outfmt option to specify how the results are presented.
  - Default value for -outfmt is 0 (zero), which produces the standard BLAST report.
  - -outfmt 6 produces a tabular report with a standard set of fields.
  - -outfmt 7 produces a tabular report with comment fields
  - -outfmt 10 produces CSV.

To customize the fields in the tabular/CSV output, see examples in slides 6-8 of [https://ftp.ncbi.nlm.nih.gov/pub/education/public\_webinars/2018/10Oct03\_Using\_BLAST/Using\_BLAST\_Well2.pdf](https://ftp.ncbi.nlm.nih.gov/pub/education/public_webinars/2018/10Oct03_Using_BLAST/Using_BLAST_Well2.pdf)

-
  - Use -outfmt 11 to save your results as a BLAST archive that you can then reformat with the blast\_formatter application. See slide 9 in [https://ftp.ncbi.nlm.nih.gov/pub/education/public\_webinars/2018/10Oct03\_Using\_BLAST/Using\_BLAST\_Well2.pdf](https://ftp.ncbi.nlm.nih.gov/pub/education/public_webinars/2018/10Oct03_Using_BLAST/Using_BLAST_Well2.pdf)

BLAST Databases.

- To see BLAST databases on a prepared GCP instance, use the comand docker run --rm ncbi/blast update\_blastdb.pl --showall pretty --source gcp
- Use update\_blastdb.pl to download the databases you need.
- Example (note that GCP is specified as source, BLASTDB\_DIR is defined and points at a directory that exists):
- docker run --rm -v $BLASTDB\_DIR:/blast/blastdb:rw -w /blast/blastdb ncbi/blast update\_blastdb.pl --source gcp swissprot\_v5
- Use blastdbcmd to interrogate the databases.
  - Summary of database: blastdbcmd -db swissprot\_v5 -info

full command with docker is docker run --rm -v $BLASTDB\_DIR:/blast/blastdb:ro -w /blast/blastdb ncbi/blast blastdbcmd -db swissprot\_v5 -info

- Print accession, scientific name, and title for all entries: blastdbcmd -db swissprot\_v5 -entry all -outfmt &quot;%a %S %t&quot;
- Print accession and title for all human (taxid 9606) entries: blastdbcmd -db swissprot\_v5 -taxids 9606 -outfmt &quot;%a %t&quot;
- Print accession, scientific name, and title for P02185: blastdbcmd -db swissprot\_v5 -entry p02185 -outfmt &quot;%a %S %t&quot;

BLAST programs (this is a brief summary)

- blastn: DNA-DNA comparisons. Add -task blastn to make it more sensitive (and much slower). Default is megablast.
- blastp: protein-protein comparisons. Add -task blastp-fast to make it faster (longer words for initial matches) and only marginally less sensitive.
- blastx: (translated) DNA query-protein comparison. Add -task blastx-fast to make it faster.
- tblastn: protein query-(translated) DNA database comparison. Add -task tblastn-fast to make it faster.
- rpsblast: protein-PSSM comparison (PSSM is position-specific-scoring matrix). Great for identifying domains in your proteins.
- rpstblastn: (translated) DNA-PSSM comparison. Great for identifying domains in your translated DNA queries.
- magicblast: mapper for DNA-DNA comparisons. Can quickly map reads (even long PacBio ones) and identify splice sites.

Documentation at [https://ncbi.github.io/magicblast/](https://ncbi.github.io/magicblast/)

- You can extract FASTAs from a BLAST DB: blastcmd -db \&lt;db\_name\&gt; -entry all -outfmt %f -out \&lt;file\_name\&gt;
- You can blast against a subset of a db using a:
  - gi list: -gilist \&lt;file\&gt;
  - Negative gi list: -negative\_gilist \&lt;file\&gt;

### **Other tools pre-installed on your VMs (including non-NCBI tools)**

#### **Dockerized**

Some VMs will have these tools installed:

- [https://github.com/NCBI-Hackathons/NCBI\_PowerTools\_Docker/blob/master/Dockerfile](https://github.com/NCBI-Hackathons/NCBI_PowerTools_Docker/blob/master/Dockerfile)

#### **Non-Dockerized**

| **hisat2** | **skesa** | **guidedassembler\_graph** | **compute-coverage** |
| --- | --- | --- | --- |
| python | pip | python3 | pip3 |
| C++ | R | Anaconda2 | conda |
| bedtools | GATK | picard | BWA |
| MiniMap 2 | BowTie 2 | EDirect | HMMer |
| samtools | bcftools | HTS JDK | HTS lib |
| STAR | abyss | plink-ng | cufflinks |
| cytoscape-impl | velvet | tophat | FastQC |
| HTSeq | mcl | muscle | MrBayes |
| GARLI | Clustal omega | Dedupe | trintyrnaseq |

## **Jupyter notebook server setup**

Based on [this cheatsheet](https://www.digitalocean.com/community/tutorials/how-to-install-anaconda-on-ubuntu-18-04-quickstart).

make sure that wget and bzip2 are installed.

1. Get the latest version from [https://www.anaconda.com/download/#linux](https://www.anaconda.com/download/#linux) (note your version or filename may be different).

$ wget https://repo.continuum.io/archive/Anaconda3-2018.12-Linux-x86\_64.sh

1. Verify your download

$ sha256sum Anaconda3-5.2.0-Linux-x86\_64.sh

1. Run the script

$ bash Anaconda3-5.2.0-Linux-x86\_64.sh

1. Create a jupyter config file

$ jupyter notebook --generate-config

1. Create a self-signed SSL certificate

$ mkdir certs`` $ cd certs/$ sudo openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout mycert.pem -out mycert.pem`

1. Generate a password hash (you will use the same password to access your jupyter notebook remotely)

$ ipythonIn [1]: from IPython.lib import passwdIn [2]: passwd() Enter password: Verify password: Out[3]: &#39;sha1:0bebc03bff39:25b6ebdkrisbf0cc3f7e6c8e0f82fcbe9e66801a&#39; Copy the sha string for later use.

1. Edit .jupyter/jupyter\_notebook\_config.py to add the following

Note the path to your mycert.pem file from step 5. Note the sha hash from step 6

######################

c.NotebookApp.allow\_remote\_access = True

# Kernel config

c.IPKernelApp.pylab = &#39;inline&#39;  # if you want plotting support always in your notebook

# Notebook config

c.NotebookApp.certfile = u&#39;/home/username/certs/mycert.pem&#39; #location of your certificate file

c.NotebookApp.ip = &#39;\*&#39;

c.NotebookApp.open\_browser = False  #so that the ipython notebook does not opens up a browser by default

c.NotebookApp.password = u&#39;sha1:ff35ddacee39:e9faaaaa1c6d5008cb50160ad1a00527c9dec09&#39;  #edit this with the SHA hash that you generated after typing in Step 9

# This is the port we opened in Step 3.

c.NotebookApp.port = 8080

 ###############

1. Start a screen instance so you can close your terminal without killing jupyter

`$ screen -DR notebook

1. Run the notebook as root

$ sudo /home/username/anaconda3/bin/jupyter notebook --config /home/username/.jupyter/jupyter\_notebook\_config.py --allow-root

1. Press ctrl+a then d to detach from the screen session.
2. Browse to [https://SERVER:8080/](https://SERVER:8080/) and enter the password you supplied in step 6, above.

- © 2019 GitHub, Inc.
- [Terms](https://github.com/site/terms)
- [Privacy](https://github.com/site/privacy)
- [Security](https://github.com/security)
- [Status](https://githubstatus.com/)
- [Help](https://help.github.com)

- [Contact GitHub](https://github.com/contact)
- [Pricing](https://github.com/pricing)
- [API](https://developer.github.com)
- [Training](https://training.github.com)
- [Blog](https://github.blog)
- [About](https://github.com/about)