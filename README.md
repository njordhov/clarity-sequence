# clarity-sequence

Sequence library for Clarity.

As Clarity is strictly typed, the library provides function variations supporting different datatypes.

Each file in `contracts` implements variations of a function for a specific sequence size, with 
a numerical suffix reflecting the number of bits in the max sequence length. For example, the contract 
named `repeat7.clar` provides functions supporting a max sequence length of 127 = `(- (pow 2 7) 1)`
represented in signatures with the placeholder `max-len`.

### repeat

Returns a list with `item` repeated `n` times, limited by the max sequence length.

The canonical variation repeats an integer `n` times, with signature:

`(repeat (n int) (item int))`

Variations:

* `(repeat-uint (n int) (item uint))`
* `(repeat-bool (n int) (item bool))`
* `(repeat-string (n int) (item (string-utf8 max-len)))`
* `(repeat-ascii (n int) (item (string-ascii max-len)))`
* `(repeat-buff (n int) (item (buff max-len)))`

### take 

Returns a sequence with the first `n` items in `seq`, or all items if there are fewer than n.

The canonical variation takes `n` items from a list of integers, with signature:

`(take (n int) (seq (list max-len int)))`

Other variations:

* `(take-uint (n int) (seq (list max-len uint)))`
* `(take-bool (n int) (seq (list max-len bool)))`
* `(take-buff (n int) (seq (buffer max-len)))`
* `(take-string (n int) (seq (string-utf8 max-len)))`
* `(take-ascii (n int) (seq (string-ascii max-len)))`

### drop

Returns a sequence with all but the first n items in seq.

The canonical version drops `n` items from a list of integers, with signature:

`(drop (n int) (seq (list max-len int)))`

Other variations:

* `(drop-uint (n int) (seq (list max-len uint)))`
* `(drop-bool (n int) (seq (list max-len bool)))`
* `(drop-buff (n int) (seq (buffer max-len)))`
* `(drop-string (n int) (seq (string-utf8 max-len)))`
* `(drop-ascii (n int) (seq (string-ascii max-len)))`

### distinct 

Returns a sequence without duplicate items.

The canonical version removes duplicate items from a list of integers:

`(distinct (seq (list max-len int)))`

Other variations:

* `(distinct-uint (seq (list max-len uint)))`
* `(distinct-bool (seq (list max-len bool)))`
* `(distinct-buff (seq (buffer max-len)))`
* `(distinct-string (seq (string-utf8 max-len)))`
* `(distinct-ascii (seq (string-ascii max-len)))`

### reverse 

Returns a sequence in reverse order.

The canonical version reverses a list of integers:

`(reverse (seq (list max-len int)))`

Other variations:

* `(reverse-uint (seq (list max-len uint)))`
* `(reverse-bool (seq (list max-len bool)))`
* `(reverse-buff (seq (buffer max-len)))`
* `(reverse-string (seq (string-utf8 max-len)))`
* `(reverse-ascii (seq (string-ascii max-len)))`
