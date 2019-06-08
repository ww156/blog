---
title: "Golang原生json性能优化"
date: 2019-05-28T08:53:27+08:00
draft: false
categories: ["golang"]
tags: ["golang", "json"]
---

### golang 原生json性能优化 
在之前的golang版本中，因为原生json包效率比较低，一直使用第三方包做json解析。
在go1.12.*版本中，测试发现golang原生json包已经比号称最快的jsoniter包，效率不相上下了，测试结果如下：
![golang json测试](https://oscimg.oschina.net/oscnet/d18b5986614f75c80a306964fc4023844ca.jpg "golang json测试")

![golang json测试](https://oscimg.oschina.net/oscnet/2b02000e563ea3623b5cc0178d38079a9d9.jpg "golang json测试")

![golang json测试](https://oscimg.oschina.net/oscnet/54b5ac36ed7df2f6ae449ef6a099fda3a31.jpg "golang json测试")

**所以，小伙伴本在高版本golang中，json解析可以直接使用原生json包了，不用引入第三方的了，更重要的是官方的，大品牌，值得信赖（=**

**最后附上测试代码，小伙伴们可以自己动手测试一下**

```go
package test

import (
	"testing"
	"encoding/json"
	"github.com/json-iterator/go"
	"fmt"
)

var (
	data = Tdata{
		Code: 0,
		Data: Data{
			Name: "小张",
			Age:  10,
		},
	}
	str = []byte(`{"code": 0,"data": {"name": "小张","age":10}}`)
	n   = 10000
	c   = 50
)

type Tdata struct {
	Code int
	Data Data
}

type Data struct {
	Name string
	Age  int
}

func BenchmarkJsonMarshal(b *testing.B) {
	b.SetParallelism(c)
	b.N = n
	b.RunParallel(func(pb *testing.PB) { //并发
		for pb.Next() {
			_, err := json.Marshal(data)
			if err != nil {
				fmt.Println(err)
			}
		}
	})
}

func BenchmarkJsonUnmarshal(b *testing.B) {
	b.SetParallelism(c)
	b.N = n
	b.RunParallel(func(pb *testing.PB) { //并发
		for pb.Next() {
			d := Tdata{}
			err := json.Unmarshal(str, &d)
			if err != nil {
				fmt.Println(err)
			}
		}
	})
}

func BenchmarkJsoniterMarshal(b *testing.B) {
	b.SetParallelism(c)
	b.N = n
	b.RunParallel(func(pb *testing.PB) { //并发
		for pb.Next() {
			_, err := jsoniter.Marshal(data)
			if err != nil {
				fmt.Println(err)
			}
		}
	})
}

func BenchmarkJsoniterUnmarshal(b *testing.B) {
	b.SetParallelism(c)
	b.N = n
	b.RunParallel(func(pb *testing.PB) { //并发
		for pb.Next() {
			d := Tdata{}
			err := json.Unmarshal(str, &d)
			if err != nil {
				fmt.Println(err)
			}
		}
	})
}

```