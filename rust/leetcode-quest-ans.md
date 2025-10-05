## Problem


## Problem

Palindrome Number

Given an integer x, return true if x is palindrome integer.
An integer is a palindrome when it reads the same backward as forward.
For example, 121 is a palindrome while 123 is not.

```
//MY SOLUTION
impl Solution {
    pub fn is_palindrome(x: i32) -> bool {
        if x < 0 || (x % 10 == 0 && x != 0) {
            return false
        }

        let (mut x, mut rev) = (x, 0);
        while x > rev {
            rev = rev * 10 + x % 10;
            x /= 10;
        }
        x == rev || x == rev / 10
    }
}

//BEST SOULUTIONS
impl Solution {
    pub fn is_palindrome(x: i32) -> bool {
        x.to_string()==x.to_string().chars().rev().collect::<String>()
    }
}
```

## Problem

PROBLEM NO - 14. Longest Common Prefix
NAME -

Description:
Write a function to find the longest common prefix string amongst an array of strings.
If there is no common prefix, return an empty string "".

Example 1:

Input: strs = ["flower","flow","flight"]
Output: "fl"
Example 2:

Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.

## Solution

```

//MY SOLUTION
impl Solution {
    pub fn longest_common_prefix(strs: Vec<String>) -> String {
       let mut lcp = strs[0].clone();
        let i = 1;
        for i in 1..strs.len() {
            let next = &strs[i];
            let mut j = 0;
            let mut temp_lcp =  String::from("");
            while j < lcp.len() && j< next.len() {
                if lcp.chars().nth(j) == next.chars().nth(j) {
                    match lcp.chars().nth(j){
                        Some(char_val) => temp_lcp.push(char_val),
                        None => break,
                    }
                } else {break};
                j += 1;
            }
            lcp = temp_lcp;
        }
        lcp.to_string()
    }
}


//BEST SOULUTIONS
impl Solution {
    pub fn longest_common_prefix(strs: Vec<String>) -> String {
      fn lcp_inplace(mut s1: String, s2: &str) -> String {
            let mut i = 0;
            for (c1, c2) in s1.chars().zip(s2.chars()) {
                if c1 != c2 {
                    break;
                }
                i += 1;
            }
            s1.truncate(i);
            s1
        }
        if strs.len() > 0 {
            strs.iter().skip(1).fold(strs[0].clone(), |acc, x| lcp_inplace(acc, &x))
        } else {
            String::from("")
        }
    }
}
//--------
impl Solution {
    pub fn longest_common_prefix(strs: Vec<String>) -> String {
        match strs.is_empty() {
            true => "".to_string(),
            _ => {
                strs.iter().skip(1).fold(strs[0].clone(), |acc, x| {
                     acc
                        .chars()
                        .zip(x.chars())
                        .take_while(|(x,y)| x == y)
                        .map(|(x, _)| x)
                        .collect()
                })
            }
        }
    }
}
//--------
impl Solution {
    pub fn longest_common_prefix(strs: Vec<String>) -> String {
        let first = &strs[0];
        let mut max_ind = first.len();

        for next in strs.iter().skip(1) {
            if let Some(((last_ind, _), _)) = first[..max_ind]
                .char_indices()
                .zip(next.chars())
                .take_while(|((_, c1), c2)| c1 == c2)
                .last()
            {
                max_ind = last_ind + 1;
            } else {
                return "".to_owned();
            }
        }
        first[..max_ind].to_owned()
    }
}
//----
impl Solution {

    pub fn longest_common_prefix(strs: Vec<String>) -> String {
    if strs.is_empty() {
        return String::from("");
    }

    let mut answer = strs[0].clone();
    for i in 1..strs.len() {
        while !strs[i].starts_with(&answer) {
            answer = answer.chars().take(answer.len() - 1).collect();
            if answer.len() == 0 {
                return String::from("");
            }
        }
    }
    return answer;

    }
}
//------
impl Solution {
    pub fn longest_common_prefix(strs: Vec<String>) -> String {
        strs.into_iter().reduce(|prev, current| {
            prev.chars()
                .zip(current.chars())
                .take_while(|(ch1, ch2)| ch1 == ch2)
                .map(|pair| pair.0)
                .collect::<String>()
        }).unwrap()
    }
}

```

## Problem

You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists in a one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
Example 2:

Input: list1 = [], list2 = []
Output: []
Example 3:

Input: list1 = [], list2 = [0]
Output: [0]

Constraints:

The number of nodes in both lists is in the range [0, 50].
-100 <= Node.val <= 100
Both list1 and list2 are sorted in non-decreasing order.

## Solution

```
impl Solution {
    pub fn merge_two_lists(
        list1: Option<Box<ListNode>>,
        list2: Option<Box<ListNode>>,
    ) -> Option<Box<ListNode>> {
        match (list1, list2) {
            (Some(l1), None) => Some(l1),
            (None, Some(l2)) => Some(l2),
            (None, None)     => None,
            (Some(l1), Some(l2)) => match l1.val <= l2.val {
                true  => Some(Box::new(ListNode {
                    val: l1.val,
                    next: Self::merge_two_lists(l1.next, Some(l2)),
                })),
                false => Some(Box::new(ListNode {
                    val: l2.val,
                    next: Self::merge_two_lists(Some(l1), l2.next),
                })),
            },
        }
    }
}
```

### Recursive solution

```
impl Solution {
    pub fn merge_two_lists(l1: Option<Box<ListNode>>, l2: Option<Box<ListNode>>) -> Option<Box<ListNode>> {
        match (l1, l2) {
            (None, None) => None,
            (Some(n), None) | (None, Some(n)) => Some(n),
            (Some(l1), Some(l2)) => {
                if l1.val >= l2.val {
                    Some(Box::new(ListNode {
                        val: l2.val,
                        next: Solution::merge_two_lists(Some(l1), l2.next)
                    }))
                } else {
                    Some(Box::new(ListNode {
                        val: l1.val,
                        next: Solution::merge_two_lists(l1.next, Some(l2))
                    }))
                }
            }
        }
    }
}
```

### Other Solution

```
use std::mem;

impl Solution {
    #[allow(dead_code)]
    pub fn merge_two_lists(l1: Option<Box<ListNode>>, l2: Option<Box<ListNode>>) -> Option<Box<ListNode>> {
        let mut result = l1;
        let mut l2 = l2;
        let mut lsmall = &mut result;
        let lbig = &mut l2;
        while lbig.is_some() {
            if lsmall.is_none() || lsmall.as_ref()?.val > lbig.as_ref()?.val {
                mem::swap(lsmall, lbig);
            }
            if lsmall.is_some() { lsmall = &mut lsmall.as_mut()?.next; }
        }
        result
    }
}
```

### other solution

```
impl Solution {
   pub fn merge_two_lists(
        mut a_ptr: Option<Box<ListNode>>,
        mut b_ptr: Option<Box<ListNode>>,
    ) -> Option<Box<ListNode>> {
        use std::mem;

        // We create two vars which are pointing to the same place in memory. While `ptr` will be continuously updated,
        // `head` will not and will keep pointing to the location of the first node.
        let mut head = None;
        let mut ptr = &mut head;

        while a_ptr.is_some() && b_ptr.is_some() {
            let ap = &mut a_ptr;
            let bp = &mut b_ptr;

            // We set `tmp` to point to the next target node we want to append.
            let mut tmp = if bp.as_ref().unwrap().val > ap.as_ref().unwrap().val { ap } else { bp };

            // We swap the data in `ptr` (the currently built up list) and the data in `tmp` (the next target node), moving the
            // currently built up list to `tmp`. `ptr` now points to the next target node.
            mem::swap(ptr, &mut tmp);

            // We swap the data in `tmp` (the currently built up list) with the data of `ptr.next`, effectively clipping
            // off the target node's tail. `tmp` now holds the tail, `ptr.next` now (only) holds the next target node.
            mem::swap(tmp, &mut ptr.as_mut().unwrap().next);

            // All the while, we only swapped what was held in memory, not what the variables were pointing to. We now move
            // the cursor along to its current `next`, the target node that we just appended.
            ptr = &mut ptr.as_mut().unwrap().next;
        }

        mem::swap(ptr, if a_ptr.is_none() { &mut b_ptr } else { &mut a_ptr });

        head
    }
}
```

## Problem

Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.
Input: head = [1,1,2,3,3]
Output: [1,2,3]

## Solution

```
impl Solution {
    pub fn delete_duplicates(head: Option<Box<ListNode>>) -> Option<Box<ListNode>> {
        if head.is_none() {
            return None;
        }
        let mut h = head;
        let mut p1 = h.as_mut().unwrap();
        while let Some(p2) = p1.next.as_mut() {
            if p1.val == p2.val {
                p1.next = p2.next.take();
            } else {
                p1 = p1.next.as_mut().unwrap();
            }
        }
        h
    }
}
```

### other soln

```
impl Solution {

    pub fn delete_duplicates(mut head: Option<Box<ListNode>>) -> Option<Box<ListNode>>
    {
        let mut curr_opt = head.as_mut();

        while let Some(curr) = curr_opt {
            let mut next_opt = curr.next.take();

            while let Some(next) = next_opt.as_mut() {
                if next.val == curr.val
                     { next_opt  = next.next.take(); }
                else { curr.next = next_opt;  break; }
            }
            curr_opt = curr.next.as_mut();
        }
        head
    }
}
```

## Problem

## Solution

## Problem

## Solution

## Problem

## Solution

```

```
