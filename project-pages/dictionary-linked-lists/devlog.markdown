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

 ### August 15, 2026
 Implemented the CSV Reader `reader.c`. I particularly liked the method of carving out fields in place by replacing `','` with `'\0'` in a buffer line, then having an array of pointers pointing to the start of each field, adjusting boundaries the same way to strip quotation marks.

 ### August 16, 2026
 Implemented the structure of the dictionary using a standard linked list, with both `*head` and `*tail` for O(1) insertions and preserving input order.
 
 ### August 17th 2026
 Implemented `int bit_cmp(const char *a, const char *b, int *cmp_count)` between two strings using the `getBit()` function that retrieves a given bit inside a string, based on index from the left. Used this to compare the keys stored in my dictionary and search the linked list. 
 
 Built a main function working from end to end: reads data from a CSV into a linked-list dictionary, takes multiple queries, and outputs all matches as well as the number of bit comparisons made.

 ### August 19th, 2026
 Added a struct to store the search results:
 ```c
 // For a search, store the matches and number of bit, node, and string
// comparisons
typedef struct {
  char *query;
  sighting_t **matches;
  int num_matches;
  int bit_cmps;
  int node_cmps;
  int str_cmps;
} search_result_t;
```
Per the specs: "Store information about the result of the search itself independently from the structure of the list"; this makes further operations easier in later stages. Decided to overallocate for `sighting_t **matches` for sake of simplicity.

Fixed one bug of forgetting to free a field. Compared memory usage from Valgrind with other students'.

