# System Files

NTFS reserves the first 16 records of the MFT for system files containing special information about the file system itself. The first record of the MFT describes the master file table itself, followed by a _MFT mirror record_. If the first MFT record is corrupted, NTFS reads the second record to find the MFT mirror file, whose first record is identical to the first record of the MFT. The locations of the data segments for both the MFT and MFT mirror file are recorded in the boot sector (Offset 0X30 and 0X38).

<figure>
<img src = "https://jor-donegal.github.io/FileSystemTheory26/images/table1.png">
<figcaption>Table 1. System Files </figcaption>
</figure>

