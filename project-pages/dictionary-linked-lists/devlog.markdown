---
layout: page
title: "Dev Log"
permalink: /projects/dictionary-linked-lists/devlog/
---
### August 9, 2026
Started the project. Decided to split it into 6 modules: the struct "sighting", a CSV reader, the dictionary, a bit comparison function, search, and main.

### August 10, 2026
 Implemented the module around `struct sighting_t`, including a create, free, and print function.
 Decided for `create_sighting` to receive raw `const char*` pointers from CSV-reader's reusable buffer, and `malloc` space internally for every string field, rather than receiving readily `malloc`'d strings for correctness and better module boundary.

 
