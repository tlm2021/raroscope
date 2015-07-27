# Introduction #

Ever faced the challenge to be able to scan RAR archives using Java? Wished the API was as simple and easy to use as the ones provided for ZIP and JAR handling in Java? Don't want  the hassles of including expensive native code into your Java application?

RARoScope is here to solve all these woes. The following lines are all you've to write to list out all the entries of a RAR file, say, "_D:/Data.rar_".

```

    // Construct the RARFile object using the file path
    RARFile file = new RARFile("D:/Data.rar");
    
    // Get the handle to the Enumeration
    Enumeration<RAREntry> entries = file.entries();
    
    // Iterate and print
    while (entries.hasMoreElements())
    {
        RAREntry entry = entries.nextElement();
        
        System.out.println(entry.getName());
    }

```

Impressed? I sure was thrilled when I first wrote the library! Go ahead, download RARoScope and start using it in your applications right now.


# What RARoScope can do? #

Exposing a simple API, RARoScope packs the following rich features.

  * **Enhanced checking for true RAR archives.**

> RARoScope ensures false RAR archives such as files with just a ".rar" extension do not interrupt further processing by reading and verifying the RAR marker header block and throwing exceptions where appropriate.

  * **A rich RAREntry class.**
> RARoScope reads almost all the information available in a RAR archive and loads them into the RAREntry instances. Following are the file metadata retrieved.
    1. Full file name including the path
    1. Date and Time the file was modified/created
    1. Compressed file size
    1. Uncompressed file size
    1. The CRC checksum for the file
    1. Whether a file is a directory
    1. The operating system on which the file was added to the archive
    1. The compression method used
    1. The RAR version required to decompress and retrieve the file

  * **Optimized for performance.**

> RARoScope has been designed to make efficient use of the underlying byte buffer so that very few I/O reads happen in each cycle. An effect of this is improved performance with very small cycle iteration times.


# What RARoScope can't do? #

However, because of various factors, RARoScope does have its limitations and can't do the following.

  * **Creating RAR archives.**

> Because of the proprietary nature of the RAR archive format, RARoScope can't be used to create RAR archives.

  * **Reading file contents/decompressing.**

> Since RARoScope has been poised as more of a "RAR scanning library" rather than a "RAR decompressor" for Java, it can't do the decompressing part. However, this is open to change in the near future. Depending on the response I get, I might implement a decompressing logic.

  * **Reading RAR entries with comments.**

> RARoScope doesn't support reading comments and entries with comments as of now.

  * **Multi-volume RAR archives.**

> RARoScope doesn't support reading multi-volume archives yet.
