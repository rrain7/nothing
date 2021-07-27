```go
func levelOrder3(root *TreeNode) [][]int {
   if root == nil{
      return nil
   }

   res := [][]int{}
   queue := []*TreeNode{root}
   level := 1
   for len(queue) != 0{
      tmp := []int{}
      que := []*TreeNode{}
      for _, node := range queue{
         tmp = append(tmp, node.Val)
         if root.Left != nil {
            que = append(que, node.Left)
         }
         if root.Right != nil{
            que = append(que, node.Right)
         }
      }
      queue =que
      if level&1 == 0 {
         tmp = reverse(tmp)
      }
      res = append(res, tmp)
      level++
   }
   return res
}

func reverse(tmp []int) []int {
   i, j := 0, len(tmp)-1
   for i<j {
      tmp[i], tmp[j] = tmp[j], tmp[i]
      i++
      j--
   }
   return tmp
}
```

​                  