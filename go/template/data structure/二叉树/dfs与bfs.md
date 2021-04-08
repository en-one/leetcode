### DFS与BFS

​	

### DFS深度搜索

- 从上到下
- 从下到上（分治法）



### BFS 广度遍历（层次遍历）

```go
func levelOrder(root *TreeNode) [][]int {

    result := make([][]int, 0)
    if root == nil {
        return result
    }

    queue := []*TreeNode{root}

    for len(queue) >0 {
        level := make([]int, 0 )
        l := len(queue)
        for i := 0; i < l ;i++ {
            node := queue[0]
            queue = queue[1:]

            level = append(level, node.Val)
            if node.Left != nil {
                queue = append(queue, node.Left)
            }
            if node.Right != nil {
                queue = append(queue, node.Right)
            }
        }
        result = append(result, level)
    }
    return result
}
```

> eg:   
>
> 102
>
> 107

