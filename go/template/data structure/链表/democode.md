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

```go
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

- 206 反转链表

> 反转一个单链表

​	思路：注意以此为扩展，其他翻转类型


```go
func reverseList(head *ListNode) *ListNode {
    var prev *ListNode
    for head != nil {
        tmp := head.Next
        head.Next = prev
        prev = head
        head = tmp
    }
    return prev
}
```

- 92 反转链表2

> 反转从位置 *m* 到 *n* 的链表。请使用一趟扫描完成反转

​	思路：先遍历到 m左边，翻转，再拼接后续，注意指针处理

```go
func reverseBetween(head *ListNode, left int, right int) *ListNode {
    if head == nil {
        return head
    }
    dummy := &ListNode{Val: 0}
    dummy.Next = head
    head = dummy

    //pre是左边不需要翻转位置
    var pre *ListNode
    for i :=0; i<left;i++ {
        pre = head
        head = head.Next
    }

    //mid 将会是反转后的尾巴，链接right右边未翻转部分
    var mid = head

    //中间翻转部分
    var next *ListNode
    for j := left; head != nil && j <= right ;j++ {
        tmp := head.Next
        head.Next = next
        next = head
        head = tmp     
    }

    pre.Next = next
    mid.Next = head
    return dummy.Next
}
```

