# extX File System Types

In 1992, the First _Extended File System_ or Ext was introduced into the Linux kernel v0.96c. This allowed for a file size of 2GB and a file system size of 2GB, with a 255-character file name. The original file system used linked lists to keep track of space and this was inefficient, slow and led to fragmentation.

The Second Extended File System or Ext2 was designed as an evolution from Ext and became the standard for Linux systems. It supported partitions of 4TB. It had support for longer names, up to 1,012 characters. _Logical block size_ could be determined at format time; the standard was 1024 but 2048 and 4096 were possible. Ext2 kept track of the state of the file system. When a file system is mounted in read/write mode, the state is set to __not clean__. When the file system is unmounted, its state is set to __clean__. At boot time, this indicates that a file system was improperly shut down and must be checked. Clean or not, a file system check also runs periodically after a set number of mounts.

Ext3, the Third Extended File System was introduced with _journaling_ to aid file system recovery and also with access control list features (ACLs). Other than that, it was a minor upgrade to Ext2. ext3 uses a journal or log to protect consistency after crashes, implemented via the _Journaling Block Device_(JBD). Journalling is a similar concept to log files in a database.

- Metadata is journaled
- File data is written to disk before the metadata is committed
- The journal entry is then cleared

Ext4 has emerged in recent years as the Fourth Extended File System to eliminate the scaling issues in Ext2/3. It introduces many modern concepts, and I would imagine learns from NTFS! The journalling is better.

- Transactions are checksummed
