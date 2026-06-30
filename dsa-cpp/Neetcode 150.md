# neetcode 150 solutions

## Arrays and Hashing

### 1. Contains duplicate
```cpp title:"My solution"
class Solution {
public:
    bool hasDuplicate(vector<int>& nums) {
        set<int> myset;
        for (int i=0; i < nums.size(); i++){
            int temp = myset.size();
            myset.insert(nums[i]);
            if (temp == myset.size()) return true;
        }
        return false;
    }
};
```

- Time Complexity: `O(nlogn)` because I used `set`, which uses binary search trees and is ordered. It's insert operation is `O(logn)` so doing it n times = `O(nlogn)`
- Space Complexity: `O(n)`, size of set.

**What can be made better?** 
- As `set` is basically BST, it's tree operations take `logn` time. Instead use a hash table (`unordered_set`) which is basically a bucket system, and it's operations are in average case `O(1)`. Close because the worst case is `O(n)` if all the elements collide into ONE bucket.

**New things:**
- `Insert`: is an API, it *returns* a `pair<iterator, bool>` where iterator is basically a pointer to either the new element added (in which case bool is `true`) or the already existing element that didn't get inserted again (bool being `false`). Thus, without checking for size in each loop, we could just check if the `pair.second` value was false.
- `count` and `contains` can become alternatives for the if condition, checking if the set contained the element already. But `insert.second` is much cleaner.
- Count: `.count(number)` gives how many times number appeared in the container. For sets and unordered_sets it is either 0 or 1 because each element is unique. So we could use this too.
- Contains (for newer C++20): `.contains(number)` is a boolean function that returns true if an element exists in the container. 
- So instead of *"did size increase?"* we could have *"is this element already in the set?"* If both output 0 (the element was not there) then insert the element and continue. If both output 1 (the element is already there!) break and return, since this is a duplicate.
- So this would eventually lead us to `O(n)` instead of `O(nlogn)`!

**Some errors that went unnoticed:**
- `nums.size()` outputs an unsigned integer `size_t` (a non-negative number) but in the `for` loop, using `int i=0` makes i a signed integer. Now usually this is fine. C++ converts i to unsigned integer during the comparison (`i < nums.size()`) and it doesn't break.
- Yet it WILL break in the case where `nums.size() = 0` and we compute `nums.size() - 1`. The output would not be -1 but some huge number.
- Fix? Use `size_t i` OR write loops using elements themselves (`for (int x : nums)`).

**Extras:**
- `size_t` is a type, just like int, float or bool. The standard library uses it for sizes and indices, which are all non-negative numbers. As `.size()` returns `size_t`, it's just better to compare it to an `i` which is `size_t` and not `int`.
- `auto` is the lazy-guy's alternative to all. At compile time (when the code is converted to assembly/machine language) auto is decided by the type of what is on the right side of it.
- So if we wanted the pair output of `set.insert()` we'd have to create `pair<unordered_set<int>::iterator, bool> result = set.insert(number);` but `auto result = set.insert(number)` is easy to write.
- Each STL container has its own iterator, and they're different because of different traversal mechanics used in each container (like set is BST, unordered_set is buckets, vector is contiguous). Each iterator is accessed by `container<type>::iterator` and follows the same three buttons. `*it` outputs object at location, `++it` takes to the next location, and `it != cont.end()` asks if we are at the end or not.
- The number -1 for unsigned integer would be 2^64 - 1 (or 2^32 - 1 for 32 bit systems).

```cpp title:"Using pair.second from the insert operation on unordered_set"
class Solution {
public:
    bool hasDuplicate(vector<int>& nums) {
        unordered_set<int> myset;
        for (size_t i=0; i < nums.size(); i++){
            auto result = myset.insert(nums[i]);
            if (result.second == false) return true;
        }
        return false;
    }
};
```
```cpp title:"using count/contains, both are same"
class Solution {
public:
    bool hasDuplicate(vector<int>& nums) {
        unordered_set<int> myset;
        for (size_t i=0; i < nums.size(); i++){
            if (myset.count(nums[i]) == 1) return true;
            myset.insert(nums[i]);
        }
        return false;
    }
};
```

### 2. Valid Anagram
```cpp title:"My solution"
class Solution {
public:
    bool isAnagram(string s, string t) {
        multiset<char> s_set;
        multiset<char> t_set;
        for (char a : s){
            s_set.insert(a);
        }
        for (char b : t){
            t_set.insert(b);
        }
        if (s_set == t_set) return true;
        return false;
    }
};
```

- Time Complexity: `O((n+m)log(n+m))` Space Complexity: `O(n+m)`
- Can be improved by using two other solutions, each using the same concept:
	- Using a hash map, which stores counts of each char
	- As characters are only 26 in number, an array of 26 size can store frequency of each character and index can be easily calculated using the trick `c - 'a` where c is a character. 
- The concept: As you go along `s` increment counts of each character, and as you go along `t` decrement counts of each character. If both were anagrams, the hashmap or array would all be containing zeroes. If any is non-zero, then both strings had different number of characters or different characters themselves.
```cpp title:"Using unordered_map, O(n)"
class Solution {
public:
    bool isAnagram(string s, string t) {
        unordered_map<char, int> freq;
        for (char a : s){
            freq[a]++;
        }
        for (char b : t){
            freq[b]--;
        }
        for (const auto& x : freq){
            if (x.second != 0) return false;
        }
        return true;
    }
};
```
```cpp title:"Using array, O(1)"
class Solution {
public:
    bool isAnagram(string s, string t) {
        int freq[26] = {0};
        for (char a : s){
            freq[a - 'a']++;
        }
        for (char b : t){
            freq[b - 'a']--;
        }
        for (int x : freq){
            if (x != 0) return false;
        }
        return true;
    }
};
```

**New:**
- `auto` vs `auto&`: `auto&` is faster because it doesn't copy the value. It refers to the original value itself. So any modifications to it will modify the original.
- An initial guard of checking both string length would save some time and allow me to write a common `for` loop for both increments and decrements.
- `const` is used to tell the compiler that this variable will not be modified. Even if you try to, it won't work.
- `const auto&` seems counter intuitive (why would I want to auto& for modifying but const to keep it same) but in reality you get best of both worlds here, as auto& saves time but const stops any accidental modifications to the original value.
- But in all seriousness, these `auto&` stuff doesn't really matter for small data types like int, char, bool but does in strings/vectors or bigger data structures. So auto is fine. Both are same speed for the small data types.

### 3. Two sum
```cpp title:"My solution"
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> hash;
        int n = nums.size();
        for (int i = 0; i < n; i++){
            hash[nums[i]] = i;
        }
        for (int i = 0; i < n; i++){
            if (hash.find(target - nums[i]) != hash.end() && i != hash[target - nums[i]]) return {min(i, hash[target - nums[i]]), max(i, hash[target - nums[i]])};
        }
        return {};
    }
};

```

**Problems I faced:**  

- Tried a two pointer approach first, incrementing and decrementing one by one but it had a major flaw of ignoring values that aren't symmetrically placed in the array
- Then I knew I had to use the `O(1)` finding ability of `hashmaps`.
- Got confused over `unordered_set` and `unordered_map`
- Had to look up how `find()` works and how if it doesn't work I have to use `hash.end()`
- Problems saving the index, at first tried `hash[nums[i]]+=i` assuming it gets created with 0 first then I could add i to it, but later realized I have to literally equate it to `i`.
- Then only some syntax errors while writing the return value. 
- Wanted to use `auto& x : nums` but needed index information so had to resort to `i`. `find()` gave out an iterator (pointer) which is not what I needed. I could dereference it and find the key (the number) using `.first` and its index (value) using `.second`
- Then faced the same index error which I fixed with a simple condition.

**What  can be made better**:  
- Even though this is `O(n)` it required *two* passes (it completed in `2n` time) it was still possible to do it in *one* pass. `n` and `2n` don't matter to Big-O, but one passes achieves the same thing in half the number of operations.
- The possibility being, *before you add the current element, check whether its complement is already in the array. If it is, return. If it's not, add the element in hash map then go to next element.*
- This also solves the same-index error as well, because since we are creating the hash map as we go, same index values don't exist. The moment we find a solution we return.
- It ALSO solves the fact that we have to return the lower index first. Since the current element is the latest one, the complement would already be before it. So its index is automatically lower.
- Why `hash.find(x)->second` is better? Because if I used `hash[x]` it would have created a value in the hash map, being 0. This creation is useless and wastes memory. `hash.find(x)->second` doesn't create anything.
- I could replace `hash.find(x) != hash.end()` with `hash.contains(x)` which is much cleaner but only available in C++20.

```cpp title:"One pass solution"
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> hash;
        int n = nums.size();
        for (int i = 0; i < n; i++){
            int x = target - nums[i];
            if (hash.find(x) != hash.end()) return {hash.find(x)->second, i};
            hash[nums[i]] = i;
        }
        return {};
    }
};
```

### 4.