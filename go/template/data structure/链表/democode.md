### demo code

**删除**

- 83 删除链表中的重复元素

> 给定一个排序链表，删除所有重复的元素，使得每个元素只出现一次。

```go
func deleteDuplicates(head *ListNode) *ListNode {
    current := head
    for current != nil {
        // 全部删除完再移动到下一个元素
        for current.Next != nil && current.Val == current.Next.Val {
            current.Next = current.Next.Next
        }
        current = current.Next
    }
    return head
}
```

- 82 删除链表中的重复元素2

> 给定一个排序链表，删除所有含有重复数字的节点，只保留原始链表中 没有重复出现的数字。

​	思路：头节点可被删除 ，使用dummy辅助

```
func deleteDuplicates(head *ListNode) *ListNode {
    if head == nil {
        return head
    }
    dummy := &ListNode{Val: 0}
    dummy.Next = head
    head = dummy

    var rmVal int
    for head.Next != nil && head.Next.Next != nil {
        if head.Next.Val == head.Next.Next.Val {
            // 记录已经删除的值，用于后续节点判断
            rmVal = head.Next.Val
            //重复的值都被删除
            for head.Next != nil && head.Next.Val == rmVal  {
                head.Next = head.Next.Next
            }
        } else {
            head = head.Next
        }
    }
    return dummy.Next
}
```

