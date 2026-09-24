# Goal

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

To retrieve the password, we need to revert the hexdump back to binary format, identify the compression format layer-by-layer, rename the file appropriately, and decompress it step-by-step until we reach plain text.


# Key Linux Concepts & Tools Used

1. **`xxd -r` (Reverse Hexdump):**
In Linux, the `xxd` program is used to both create hex dump files as convert those hex dump files back into their original forrmats. Converts a text file containing hexadecimal values back into a raw binary file.
2. **`mkdir` (short for "make directory"):**
Is a command used to create new folders in an operating system.
3. **`file` (Determine File Type):**
Reads the file's header (Magic Bytes) to determine its actual file type, regardless of its extension.
4. **`mv` (Move / Rename):**
Renames files so that decompression tools like `gzip` recognize them.
5. **`gzip -d` / `bzip2 -d` / `tar -xf`:**
Decompression utilities for `.gz`, `.bz2`, and `.tar` archives, respectively.
6. **`mktemp -d`:**
Is a command used to create a uniquely named temporary directory with secure permissions to prevent file conflicts and unauthorized access.


# Step-by-Step Solution

## Step 1: Set up a working directory

Because `/home/bandit12/` is read-only, you must create a temporary workspace inside `/tmp/` where you have full read and write permissions.

```bash
mkdir /tmp/my_work_dir
cd /tmp/my_work_dir
cp ~/data.txt .

```

## Step 2: Revert the Hexdump

<img width="799" height="534" alt="Screenshot from 2026-09-24 13-29-56" src="https://github.com/user-attachments/assets/d8e54a9e-c82f-4d6b-b0d4-e698be32c0d7" />

The file `data.txt` contains text representation of hex values. We convert it back to a binary file named `data` using `xxd -r`:

```bash
xxd -r data.txt data

```

## Step 3: Peeling the Compression Layers (Iterative Decompression)

Now we repeat a simple 3-step loop until we reach plain text:

1. Run `file <filename>` to check the compression type.
2. Rename the file using `mv` to give it the correct extension required by the tool.
3. Extract/Decompress the file.


### Layer 1: gzip

```bash
file data
# Output: data: gzip compressed data...

mv data data.gz
gzip -d data.gz

```

*Resulting file:* `data`


### Layer 2: bzip2

```bash
file data
# Output: data: bzip2 compressed data...

mv data data.bz2
bzip2 -d data.bz2

```

*Resulting file:* `data`


### Layer 3: gzip

```bash
file data
# Output: data: gzip compressed data...

mv data data.gz
gzip -d data.gz

```

*Resulting file:* `data`


### Layer 4: tar archive

```bash
file data
# Output: data: POSIX tar archive (GNU)...

mv data data.tar
tar -xf data.tar

```

*Resulting file extracted:* `data5.bin`


### Layer 5: tar archive

```bash
file data5.bin
# Output: data5.bin: POSIX tar archive (GNU)...

mv data5.bin data5.tar
tar -xf data5.tar

```

*Resulting file extracted:* `data6.bin`


### Layer 6: bzip2

```bash
file data6.bin
# Output: data6.bin: bzip2 compressed data...

mv data6.bin data6.bz2
bzip2 -d data6.bz2

```

*Resulting file:* `data6`


### Layer 7: tar archive

```bash
file data6
# Output: data6: POSIX tar archive (GNU)...

mv data6 data6.tar
tar -xf data6.tar

```

*Resulting file extracted:* `data8.bin`


### Layer 8: gzip

```bash
file data8.bin
# Output: data8.bin: gzip compressed data...

mv data8.bin data8.gz
gzip -d data8.gz

```

*Resulting file:* `data8`


## **Step 4: Read the Password**

Check the file type one last time:

```bash
file data8
# Output: data8: ASCII text

cat data8

```

The output printed on your terminal is the password for **Bandit Level 13**.
```bash

```

# **Summary Table of Decompression Commands**

| Format | Extension Required | Command to Decompress |
| --- | --- | --- |
| **Gzip** | `.gz` | `gzip -d <filename>.gz` |
| **Bzip2** | `.bz2` | `bzip2 -d <filename>.bz2` |
| **Tar Archive** | `.tar` | `tar -xf <filename>.tar` |
