:orphan:

BGZip
=============

1 contributor · 2 versions

:ID: ``bgzip``
:Python: ``janis_bioinformatics.tools.htslib.bgzip.bgzip_1_2_1 import BGZip_1_2_1``
:Versions: 1.9, 1.2.1
:Container: biodckrdev/htslib:1.2.1
:Authors: Michael Franklin
:Citations: None
:Created: 2018-12-24
:Updated: 2019-01-24
:Required inputs:
   - ``file: VCF``
:Outputs: 
   - ``out: stdout<CompressedVCF>``

Documentation
-------------

URL: `http://www.htslib.org/doc/bgzip.html <http://www.htslib.org/doc/bgzip.html>`_

bgzip – Block compression/decompression utility

Bgzip compresses files in a similar manner to, and compatible with, gzip(1). The file is compressed 
into a series of small (less than 64K) 'BGZF' blocks. This allows indexes to be built against the 
compressed file and used to retrieve portions of the data without having to decompress the entire file.

If no files are specified on the command line, bgzip will compress (or decompress if the -d option is used) 
standard input to standard output. If a file is specified, it will be compressed (or decompressed with -d). 
If the -c option is used, the result will be written to standard output, otherwise when compressing bgzip 
will write to a new file with a .gz suffix and remove the original. When decompressing the input file must 
have a .gz suffix, which will be removed to make the output name. 
Again after decompression completes the input file will be removed.

------

Additional configuration (inputs)
---------------------------------

==========  =================  ========================================================================================================================================================================================================================================================
name        type               documentation
==========  =================  ========================================================================================================================================================================================================================================================
file        VCF                File to bgzip compress
offset      Optional<Integer>  b: Decompress to standard output from virtual file position (0-based uncompressed offset). Implies -c and -d.
stdout      Optional<Boolean>  c: Write to standard output, keep original files unchanged.
decompress  Optional<Boolean>  d: Decompress.
force       Optional<Boolean>  f: Overwrite files without asking.
help        Optional<Boolean>  h: Displays a help message.
index       Optional<Boolean>  i: Create a BGZF index while compressing. Unless the -I option is used, this will have the name of the compressed file with .gzi appended to it.
indexName   Optional<File>     -I: Index file name.
compress    Optional<Integer>  l: Compression level to use when compressing. From 0 to 9, or -1 for the default level set by the compression library. [-1]
reindex     Optional<Boolean>  r: Rebuild the index on an existing compressed file.
rebgzip     Optional<Boolean>  g: Try to use an existing index to create a compressed file with matching block offsets. Note that this assumes that the same compression library and level are in use as when making the original file. Don't use it unless you know what you're doing.
size        Optional<Integer>  s: Decompress INT bytes (uncompressed size) to standard output. Implies -c.
threads     Optional<Integer>  @: Number of threads to use [1].
==========  =================  ========================================================================================================================================================================================================================================================

