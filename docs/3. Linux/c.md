# iNodes

Almost every UNIX file system uses the same concepts for file system organisation.

Every file is represented by a metadata structure called an _I-node_. 
An I-node stores information about a regular file, directory, or other file system object in 128-byte records:

- File type (executable, block special etc.)
- Permissions (read, write etc.)
- Owner, Group
- File Size
- File access, change and modification time, File deletion time.
- Number of links (soft/hard)
- Extended attribute such as append only.
- Access Control List (ACLs)

A directory I-node is a list of files and directories. 
Its purpose is to make a link between file names and I-node numbers. 
In Ext2/3 there is a limit of 32,768 subdirectories and a limit of 10-15,000 files per directory.

<figure>
<img src = "https://jor-donegal.github.io/FileSystemTheory26/images/fig9.png">
<figcaption>Fig 9. An iNode. </figcaption>
</figure>

I can use __ls__ to find the iNode number of the current and parent directory or of any file. 

````
johnoraw@RPi5-DataStore1:~ $ ls -id ./
14417922 ./
johnoraw@RPi5-DataStore1:~ $ ls -id ../
14417921 ../
johnoraw@RPi5-DataStore1:~ $ ls -id main.py 
14549744 main.py
````

<figure>
<img src = "https://jor-donegal.github.io/FileSystemTheory26/images/table2.png">
<figcaption>Table 2. iNode numbers. </figcaption>
</figure>

All files and directories can be listed with their names and their I-node numbers. The block locations for each files and directory can then be looked up in the I-Node table. As the filenames are stored in a directory entry and the I-nodes are stored separately, any I-node can have more than one name. This is very useful and gives us the concept of a _link_, where multiple directory entries point at the same I-node. The I-node in turn has a link counter which keeps track of the number of directory entries pointing at the I-node.

When a user deletes a file, this link count is decremented. When the link count reaches zero, the I-node is deallocated. These are called _hard links_ and because they use I-node numbers, they cannot cross a file system boundary (as I-nodes will only be unique per file system).

Where we need links to cross system boundaries, we use _symbolic links_. These are just files which contain a file name. When the kernel encounters a symbolic link, it replaces the link with the contents of the file and continues whatever request it was servicing.