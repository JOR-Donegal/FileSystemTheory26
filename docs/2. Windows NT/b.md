# NTFS

In the early 1990s, Microsoft had realised that their original DOS/Windows technology had reached the end of feasible development and that they needed new beginnings. The Windows New Technoloy (NT) project was successful and with it came a new file system to replace FAT. FAT dated back to the 1970 and was archaic and obsolete as a server file system; it remains to this day as a suitable file system for removable media. 

HPFS was designed for use with OS/2 and was better, but suited for desktop, not server environments. 

Microsoft learned a great deal from the development of HPFS and these lessons were implemented in their new file system (NTFS).

NTFS was written by a team headed by Tom Miller.

It was built to be:

- Reliable, with metadata redundancy and fault tolerance.
- Secure.
- Recoverable using transaction processing, _journaling_.

It was intended to be scalable to cope with large volumes, partitions, disks, and files.

- 2^64^ files of 2^64^ bytes long
- On Windows Server 2012 the maximum file size was 256TB
- 2^64-1^ Clusters
- With a standard cluster size of 4KB, a volume can be just under 16TB.

NTFS was not designed for removable media as it uses a _lazy write_ scheme. 
The cache manager deliberately buffers and delays writing data to disk to boost performance.
Grouping many small writes into fewer big writes is much faster.
NTFS journals metadata, not file contents, after a crash the file system structure is consistent but recent file data may be missing or corrupt.

The file system is structured as a database and uses the concept of transactions in the form of a journal.

- The metadata file $LogFile is used to log changes to metadata.
- Changes to files and directories are recorded in the Update Sequence Number Journal (USN).

As with the Apple file systems of the time, there are multiple _data streams_, each attribute is a stream.

_Compression_ was built into the original standard and _encrypted directories_ (EFS) were added later. _Sparse files_ can be accommodated; these are files with empty space within them. Then empty space is recorded but does not take up storage space.

NTFS support _Volume Shadow Copy_ (VSC) to allow earlier versions of files to be recovered. This is useful for recovering files and used by file system backups to access files which are in use and locked.

_Transactional NTFS_ allows a transaction involving a group of files to be treated as a single transaction, in the event of the transaction not completing, the entire transaction can be rolled back.

Security was introduced. Two sets of _Access Control Lists_ (ACLs) are defined, one for _discretionary access control_ (DAC) and the other for _mandatory access control_ (DAC). Read about DAC and MAC to fully understand, but simplified, with DAC the user decides on permissions. With MAC, system policies determine permissions.

_Disk Quotas_ were introduced to limit user’s exploitation of disk space.