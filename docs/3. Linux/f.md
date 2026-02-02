# Double Indirect Pointers

If the files are larger, the fourteenth block can point to a block, which in turn points to other blocks of pointers; this is a doubly indirect pointer. 
We can now address a file size of 12 + 1,024 + (1,024*1,024) blocks, or about 4.3GB.

<figure>
<img src = "https://jor-donegal.github.io/FileSystemTheory26/images/fig12.png">
<figcaption>Fig 12. Double indirect Pointers. </figcaption>
</figure>