# DOS and FAT

When the PC first emerged, it did so with the _File Allocation Table_ or FAT file system. Disks were divided into sectors of 512 bytes and this is the smallest block of data which could be stored. The file system had a fixed format, where the first sector of the file system contained meta-data about the whole disk. If the disk was bootable, the first three bytes contained a machine code __jump__ instruction, pointing at the operating system’s _boot loader_. 

The FAT itself was a table of pointers to sectors which contained file data and a separate table existed called a _directory_, with the names of the files. Content was stored in _clusters_

- Sectors were 512 bytes 
- Cluster = 2 or more * consecutive sectors 
- The first cluster address is cluster 2 
- If file > 1 cluster, locations found using _File Allocation Table_ (FAT)

<figure>
<img src = "https://jor-donegal.github.io/FileSystemTheory26/images/fig1.png">
<figcaption>Fig 1. FAT partition layout</figcaption>
</figure>

When FAT12 emerged in 1980 it was used on single sided, single density disks with a typical capacity of 180KB. The naming was the crude 8.3 format where a filename was something like JOHNORAW.TXT and no security or ownership information lived in the file system.

For a worked example demonstrating FAT, take a look at [this video](https://media.heanet.ie/page/364e4f359aae43d2b6d0d305a8f9c3d1) from 2019.

The early hard drives which appeared with PC technology quickly outstripped the capabilities of the operating systems we had at the time, and of the file systems they implemented to keep track of where files were saved. The maximum capacity of FAT was 512 * 216 or 32MB, so when I got my first 120MB hard drive, I had a problem! There was no way to format it so that I could use more than 32MB, the file system just could not map it.

In 1983 the concept of a _partition_ was introduced by IBM to PCs with version 2 of PC-DOS. Partitions allowed us to break up a hard drive into separate logical areas, each of which could contain its own file system. To the operating system, it appeared as if it had more than one hard drive, each with its own separate file system. 