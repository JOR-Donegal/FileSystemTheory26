# Triple indirect Pointers

Finally, the fifteenth pointer can point to a block, which points to other blocks, which points to other blocks, for a triple indirect pointer. 
We can now address a file size of 12 + 1,024 + (1,024*1,024) + (1,024*1,024*1,024) blocks, or about 4.4TB.

<figure>
<img src = "https://jor-donegal.github.io/FileSystemTheory26/images/fig13.png">
<figcaption>Fig 13. Triple indirect Pointers. </figcaption>
</figure>

In the 1980s when these concepts were first developed, these file sizes were unimaginable. 
We now need to work with files greater than this size. 
We will look at that when we discuss _extents_ under Ext4.