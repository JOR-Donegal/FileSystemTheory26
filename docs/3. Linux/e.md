# Indirect Pointers

Where files are bigger, we can use the thirteenth pointer, the indirect pointer. 
This points at a 4KB block which itself contains pointers. 
Block pointers are all 4 bytes quantities, so 1,024 blocks can be addressed in this way. 
We can now store file data in 12 + 1,024 blocks, or around 4.2MB.

<figure>
<img src = "https://jor-donegal.github.io/FileSystemTheory26/images/fig11.png">
<figcaption>Fig 11. Indirect Pointers. </figcaption>
</figure>