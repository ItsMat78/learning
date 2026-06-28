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
