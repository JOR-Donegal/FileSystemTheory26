# Direct Pointers

The address of the data blocks which contain the file data are held in the I-node; there are 15 pointers but only the first 12 can be used as direct pointers. 
So in a file system with 4KB blocks, files of up to 48KB can be addressed.

<figure>
<img src = "https://jor-donegal.github.io/FileSystemTheory26/images/fig10.png">
<figcaption>Fig 10. Pointers. </figcaption>
</figure>