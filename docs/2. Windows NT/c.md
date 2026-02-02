# Volume Structure

A _volume_ is the largest unit of structure in NTFS. Each file on an NTFS volume is represented by a record in the _Master File Table_ or MFT.

A _system file_ is one used by the file system to store its metadata and to implement the file system. System files are placed on the volume by the _Format_ utility. Everything in NTFS is a file.

<figure>
<img src = "https://jor-donegal.github.io/FileSystemTheory26/images/fig2.avif">
<figcaption>Fig 2. NTFS partition layout</figcaption>
</figure>

## $boot
On an NTFS partition, the first 16 sectors are allocated to the partition boot sectors and the file __$boot__.

The first sector contains meta-data similar to other file systems like FAT, with a _BIOS parameter block_ (BPB) so it really is a _boot sector_ like FAT has.

_Bootstrap_ code exists from 0x54.

<figure>
<img src = "https://jor-donegal.github.io/FileSystemTheory26/images/fig3.png">
<figcaption>Fig 3. First sector layout. </figcaption>
</figure>

## The BIOS Parameter Block

The BIOS Parameter Block is similar to the reserved are at the start of a FAT partition. The fields starting at 0x0B, 0x0D, 0x15, 0x18, 0x1A, and 0x1C match those on FAT16 and FAT32 volumes.

<figure>
<img src = "https://jor-donegal.github.io/FileSystemTheory26/images/fig4.png">
<figcaption>Fig 4. BPB. </figcaption>
</figure>

## Extended BIOS Parameter Block

The __Extended BIOS Parameter Block__ holds additional fields for locating the MFT, the most important metadata structure in NTFS. The MFT is not located in a fixed sector (although it almost always is by default).

<figure>
<img src = "https://jor-donegal.github.io/FileSystemTheory26/images/fig5.png">
<figcaption>Fig 5. EBPB. </figcaption>
</figure>

## Initial Programme Loader (IPL)
There are 15 sectors reserved for the _Initial Program Loader_ (IPL) code. 15 * 4,096 = 61,440 bytes for the IPL.