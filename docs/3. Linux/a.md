# The Virtual File System

Before introducing new file system types, an additional layer of abstraction was added to Linux, the _Virtual File System_ or VFS. This was not a new concept and dates back at least to SunOS in the 1980s.

This layer allows file system calls to be made to the VFS, rather than to the physical file systems code. These eases migration to new file system types and to mixed file systems on a single system. The VFS defines functions which every file system will implement. File system types are defined in the kernel.

When a file system is to be _mounted_, a function is called which reads the _superblock_ from the file system, initializes variables, and returns a descriptor to the VFS.

Linux can deal with a range of local file systems, or with network-based file systems like NFS. In more recent times, code has been implemented for iSCSI and Fibre Channel.

<figure>
<img src = "https://jor-donegal.github.io/FileSystemTheory26/images/fig8.png">
<figcaption>Fig 8. The VFS. </figcaption>
</figure>
