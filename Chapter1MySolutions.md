# Chapter 1: Arrays and Strings

### Interview Questions:

##### 1.1: Is Unique: Implement an algorithm to determine if a string has all unique characters. What if you cannot use additional data structures?

Create a hash table using the _Chaining with Linked Lists_ approach, with an array of length equal to the number of characters in the given alphabet. Iterate over the string, adding each character to the hash table - if at any point a collision occurs, a character was found more than once. Assuming each of the characters are using a character encoding like ASCII, the hash function can be placed uniquely into the array.

We can use a bit vector to determine the uniqueness of all characters in a string. Assuming `a = 0000...0001` with a Bit Vector of length 128, we can create a variable Bit Vector `current`. Iterating over each character, we perform the bitwise operation `result = current & cha` where `cha` is the Bit Vector representation of the character. If the value of `result` is equal to 0, then we update `current = current | cha`. Otherwise, we know there to be a duplicate occurence of the same character.


##### 1.2: Check Permutation: Given two strings, write a method to determine if one is a permutation of the other.

For one string to be a permutation of the other, it must contain all the characters used by the other with a differing order.

Brute force approach: Sort both strings, and compare the resultant sorted strings.

The optimal time complexity approach is as follows: Create an array of length 128 (Based on number of ASCII characters), and increment the value stored at each index upon encountering a character whose ASCII code corresponds to said index, for the first string. Then, iterating over the characters in the second string, decrement the value at the array index corresponding to the character code - if this value is ever negative, the strings are not permutations of one another.


##### 1.3: URLify: Write a method to replace all spaces in a string with '%20'. You may assume that the string has sufficient space at the end to hold the additional characters, and that you are given the 'true' length of the string.


We edit the string (in this case, character array) from the end and work backwards, though we initially count the number of spaces and for each found space, we increase our starting index by 2. Then, iterating backwards through the input character array, if we encounter a `whitespace` we insert `%20` otherwise we copy the element directly to the character array.