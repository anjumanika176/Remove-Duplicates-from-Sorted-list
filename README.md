# Remove-Duplicates-from-Sorted-list
LeetCode 83 Remove Duplicates from Sorted List solution in Python
# LeetCode 83: Remove Duplicates from Sorted List

## Problem
Given the `head` of a sorted linked list, delete all duplicates so that each element appears only once.
Return the linked list sorted as well.

## Examples

| Input | Output |
|-------|--------|
| `head = [1,1,2]` | `[1,2]` |
| `head = [1,1,2,3,3]` | `[1,2,3]` |

## Constraints
- The number of nodes in the list is in the range `[0, 300]`.
- `-100 <= Node.val <= 100`
- The list is sorted in ascending order.

## Approach
Because the list is sorted, duplicate values are always next to each other.
So one pointer `p` is enough. Walk through the list and compare the current node with the next node:

- If the values are **equal**, the next node is a duplicate. Remove it with `p.next = p.next.next`.
- If the values are **different**, move forward with `p = p.next`.

`p` is moved forward only in the `else` branch. After removing a duplicate, `p` stays on the same node,
because the new next node can also be a duplicate (for example `[1,1,1,2]`).

The loop condition `while p and p.next` handles an empty list and a single-node list,
and it makes sure `p.next.val` is never read when `p.next` is `None`.

The head is never removed (the first node is never a duplicate), so `head` is returned at the end.

### Walkthrough: `[1,1,2,3,3]`

| Step | p.val | p.next.val | Action | List |
|------|-------|------------|--------|------|
| 1 | 1 | 1 | remove duplicate | `1 -> 2 -> 3 -> 3` |
| 2 | 1 | 2 | move forward | `1 -> 2 -> 3 -> 3` |
| 3 | 2 | 3 | move forward | `1 -> 2 -> 3 -> 3` |
| 4 | 3 | 3 | remove duplicate | `1 -> 2 -> 3` |
| 5 | 3 | none | loop ends | `1 -> 2 -> 3` |

### Edge cases

| Case | Result |
|------|--------|
| Empty list `[]` | `None` is returned, the loop does not run |
| One node `[5]` | `[5]`, the loop does not run |
| All equal `[1,1,1]` | `[1]` |
| No duplicates `[1,2,3]` | `[1,2,3]` |


```

## Complexity
- Time: O(n), the list is traversed once
- Space: O(1), the list is edited in place

## Concepts Used
- Singly linked list traversal
- Deleting a node by relinking (`p.next = p.next.next`)
- Two-condition loop (`p and p.next`)

## Language
Python 3 

## Link
https://leetcode.com/problems/remove-duplicates-from-sorted-list
