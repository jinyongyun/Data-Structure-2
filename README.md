# Data-Structure-2
Data structure from last test
Maps & Dictionaries

Maps
􀂉 A map models a searchable collection of
key-value entries
􀂉 The main operations of a map are for
searching, inserting, and deleting
items
􀂉 Multiple entries with the same key are not
allowed
􀂉 Applications:
􀂄 address book
􀂄 student-record database

Dictionary
􀂉 Multiple items with the same key are
allowed
􀂉 Applications:
􀂄 word-definition pairs
􀂄 credit card authorizations
􀂄 DNS mapping of host names (e.g.,
inha.ac.kr) to internet IP addresses (e.g.,
165.246.13.102)

Entry ADT of Map & Dictionary
􀂉 An entry stores a key-value pair (k,v)
􀂉 Methods:
􀂄 key(): return the associated key
􀂄 value(): return the associated value
􀂄 setKey(k): set the key to k
􀂄 setValue(v): set the value to v

The Map ADT
􀂉 find(k): lookup an entry with key k
􀂄 if there is an entry with key k, returns a pointer to
it, else returns the special iterator end
􀂉 put(k, v): insert an entry with key k and
value v
􀂉 erase(k): remove an entry with key k
􀂉 size(), empty(), begin(), end(): other basic operations

Example of Map
Operation Output Map
empty() true Ø
put(5,A) [(5,A)] (5,A)
put(7,B) [(7,B)] (5,A),(7,B)
put(2,C) [(2,C)] (5,A),(7,B),(2,C)
put(8,D) [(8,D)] (5,A),(7,B),(2,C),(8,D)
put(2,E) [(2,E)] (5,A),(7,B),(2,E),(8,D)
find(7) [(7,B)] (5,A),(7,B),(2,E),(8,D)
find(4) end (5,A),(7,B),(2,E),(8,D)
find(2) [(2,E)] (5,A),(7,B),(2,E),(8,D)
size() 4 (5,A),(7,B),(2,E),(8,D)
erase(5) 􀂲 (7,B),(2,E),(8,D)
erase(2) 􀂲 (7,B),(8,D)
find(2) end (7,B),(8,D)
empty() false (7,B),(8,D)

A Simple List-Based Map
􀂉 We can efficiently implement a map using an
unsorted list
􀂄 We store the items of the map in a list S (based
on a doubly-linked list), in arbitrary order

Find Algorithm in List-based Map
Algorithm find(k):
for each p in [S.begin(), S.end()) do
if p􀁯key() = k then
return p
return S.end() {there is no entry with key equal to k}


Put Algorithm in List-based Map
Algorithm put(k,v):
for each p in [S.begin(), S.end()) do
if p􀁯key() = k then
p􀁯setValue(v)
return p
p = S.insertBack((k,v)) {there is no entry with key k}
n = n + 1 {increment number of entries}
return p

Erase Algorithm in List-based Map
Algorithm erase(k):
for each p in [S.begin(), S.end()) do
if p.key() = k then
S.erase(p)
n = n - 1 {decrement number of entries}

Performance of a List-Based Map
􀂉 Performance:
􀂄 put takes O(n) time since we need to determine whether it is
already in the sequence
􀂄 find and erase take O(n) time since in the worst case (the
item is not found) we traverse the entire sequence to look
for an item with the given key
􀂉 The unsorted list implementation is effective only for
maps of small size or for maps in which puts are the
most common operations, while searches and
removals are rarely performed (e.g., historical record
of logins to a workstation)


Major Implementation
for Maps and Dictionaries
􀂉 Hash Table
􀂄 Only need to look up entries based on their keys
􀂄 O(1) expected time for:
􀂊 find, insert, delete
􀂊 Although O(n) in the worst case time (still not very bad news)
􀂉 Binary Search Tree
􀂄 O(h) time for: (i.e., O(log n) for a balanced tree)
􀂊 find, insert, delete
􀂄 Not only look up values, but also find values based on their
orderings
􀂊 e.g., find the value with the smallest key >= k
find the value with the largest key <= k
