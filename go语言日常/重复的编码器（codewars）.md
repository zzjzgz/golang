```go
//codewars-----Duplicate Encoder--------------------------------------------------------------------------------------
//题目:
	//这个练习的目标是将一个字符串转换为一个新字符串，其中新字符串中的每个字符都是“(”，
	//如果该字符只在原始字符串中出现一次，或者“)”，
	//如果该字符在原始字符串中出现不止一次。当确定一个字符是否重复时，忽略大小写
//案例
	//"din"      =>  "((("
	//"recede"   =>  "()()()"
	//"Success"  =>  ")())())"
	//"(( @"     =>  "))((" 
package main

import (
	"fmt"
)

func main() {
	var s string
	fmt.Scanf("%s", &s)
	fmt.Printf("%s",DuplicateEncode(s))
}
func DuplicateEncode(word string) string {
	b:=make([]byte,len(word))              //创立一个字符切片---字符串中的字母属于字符
	for i:=0;i<len(word);i++{
		s:=word[i]
		if word[1]>='A' &&  word[i]<='Z'{       //全部转成小写
			s=s-'A'+'a'                      
            //--s = 原来的字母--如果 s 不是大写直接赋值给字符切片------------------------
			//-----如果是大写的就减去 A 的ascll码来获取位置在加上初始小写字母a 的ascll
		}
		b[i]=s
	}
	var str string=string(b[ : ]) //用字符串代替 b 来进行循环判断-----可以防止赋值过程对 if 判断有干扰
	for j:=0;j<len(str);j++{
		var num int
		for k:=0;k<len(str);k++{
			if str[j]==str[k]{
				//fmt.Printf("%c\n",str[j])
				num++                   //重复的次数
			}
		}
		if num==1{
			b[j]='('
		}else{
			//fmt.Printf("%c",b[j])
			b[j]=')'
		}
	}
	//fmt.Printf("%c\n",b)
	return string(b[:])              //字符数组转字符串
}
```

