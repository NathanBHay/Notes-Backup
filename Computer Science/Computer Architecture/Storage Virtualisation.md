Storage virtualisation are a set of techniques to improve efficiency or the recovery ability of multiple [[Memory#Secondary Memory|drives]], by viewing the storage as a singular pool. To achieve this a disc controller is implemented within software or hardware. Storage virtualisation is commonly implemented on servers and high-performance computers. There are two approaches to storage virtualisation which are:
- **Block virtualisation** which views the data of drives as a set of slices, or blocks. From this the file system is optimised using these blocks as units.
- **File virtualisation** (**NAS virtualisation**) deals with groups of files as the primary unit.

# RAID
Redundant Array of Inexpensive Disks (**RAID**) is a suite of mass storage array techniques (called levels) that are controlled with controller software. 

| Level  | Min Drives | Fault Tolerance | Space Eff                  |
| ------ | ---------- | --------------- | -------------------------- |
| RAID 0 | 2          | None            | 1                          |
| RAID 1 | 2          | n-1 Drives      | $\frac{1}{n}$              |
| RAID 2 | 3          | 1 Drive         | $1-\frac{1}{n}\log_2(n+1)$ |
| RAID 3 | 3          | 1 Drive         | $1-\frac{1}{n}$            |
| RAID 4 | 3          | 1 Drive         | $1-\frac{1}{n}$            |
| RAID 5 | 3          | 1 Drive         | $1-\frac{1}{n}$            |
| RAID 6 | 4          | 2 Drives        | $1-\frac{2}{n}$            |
## Array Striping (RAID 0)
Array striping stores all data as a set of slices called *stripe units* that are partitioned across multiple drives. This improves the speed of memory access as drives are written to simultaneously to keep files. RAID 0 is the fastest storage approach as data is accessed concurrently. Despite this drive failure destroys the file system.

## Mirroring (RAID 1)
Mirroring is a way of ensuring reliability of hard-drives through creating exact copies of a drives. This can be done with the use of stripe units in cases where more storage space is required. This enables the drives to recovery data as long as one effective drive hasn't failed. Given you use the drive that accesses the data first, mirroring can be faster on average than having a single drive.

## RAID 2
RAID 2 uses byte-level stripes has the presence Hamming code error correction segments. Data is striped which means sequential bits are on different drives. This is used to restore some data in failure.

## RAID 3
RAID 3 uses byte-level stripes with redundancy bytes which allow for recovery of drives. A trait of RAID 3 is that it requires all disks to by synchronised, meaning only one request can be handled at once. Due to this it is hardly used in practice due to it being less effective than other variants.

## RAID 4
RAID 4 uses block-level striping with dedicated parity disks. It provides good performance for random reads but due to the parity disks requires all writes to be synchronised.

## RAID 5
RAID 5 uses distributed parity blocks across block interleaved drives to enable it to recover from the loss of a hard-drive within the network. It is the most widely used approach as it is generic enough to be applied in any situation. 

## RAID 6
RAID 6 is an expansion upon RAID 5 where in addition to distributed check blocks that use bit-wise XOR, it also uses Reed-Solomon error correcting codes. This enables it to recover from the failure of two disks, at the cost of double the amount of space used in checks.