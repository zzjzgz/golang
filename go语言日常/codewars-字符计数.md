＃#一，译文意思：

​				1、找出一串字符串中字母与数字出现的次数>=2的字符（不分大小写）。

## 二、解题思路：

​				1、题目明确规定不区分大小写--我们可以全部转换为小写来排除干扰。

​				2、利用golang中的字典可以遍历出字符出现的次数。

​				3、最后在对字典进行遍历。

 ## 我的解答

```go
func duplicate_count(s1 string) int {
  var num int
  b := make([]byte, len(s1))
  //创建切片
  for i, _:= range s1{
    s := s1[i]
    if 'A' <= s && s <= 'Z' {
      s = s - 'A' + 'a'          //减去大写的'A'可以获得ascll差值再加上 'a'的ascll值来定位字母
    }
    b[i] = s
  }
  //对字符串处理全为小写
  stat := map[rune]int{}          //创建字典
  for _, ch := range string(b) {
    if (ch >= 'a' && ch <= 'z') || (ch >= '0' && ch <= '9'){
      stat[ch]++
    }
  }
  for _, v := range stat{     //字典的遍历---v为字符次数 
    if v>1{
      num++
    }
  }
  return num
}
```


## 字典

```go
  var  stat = map[rune]int{}      
```

​			1、 这里创建了一个字符的字典----->rune-代表一个 UTF-8 字符，当需要处理中文、日文或者其他复合字符时，						则需要用到 rune 类型。rune 类型等价于 int32 类型。
​			2、这里的97为---a的ascll码（后面依次推）。也就是 a 出现了4次、b 出现了3次、c出现了2次、d出现了1次。

## 结语
​			1、万事开头难
​			2、但是：世上无难事，只怕有心人
