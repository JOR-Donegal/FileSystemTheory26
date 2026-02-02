# MFT
NTFS keeps track of the contents of a volume using the MFT, which is a relational database. Space is allocated as clusters (2^n^ sectors) and all storage uses Logical Cluster Numbers (LCNs). A copy of the MFT is kept elsewhere in the file system; this is the __$MFTMirror__.

The MFT keeps entries for every file in the system. The first 16 entries in the MFT are reserved for system metadata, which is all stored as files.

At the very least, each MFT entry must have
- A header
- Attribute type 16: Standard Information
- Attribute type 48: File Name
- Attribute type 128: Data

<figure>
<img src = "https://jor-donegal.github.io/FileSystemTheory26/images/fig6.png">
<figcaption>Fig 6. An MFT Entry. </figcaption>
</figure>

NTFS views files as a collection of attributes and directories as a file with slightly different attributes.

<figure>
<img src = "https://jor-donegal.github.io/FileSystemTheory26/images/fig7.png">
<figcaption>Fig 7. The MFT. </figcaption>
</figure>

The rows of the MFT correspond to individual files, the columns correspond to file attributes.