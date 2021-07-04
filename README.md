# jodatime

[![GoDoc](https://godoc.org/github.com/abelli5/jodatime?status.svg)](https://godoc.org/github.com/tengattack/jodatime)
[![Build Status](https://travis-ci.org/abelli5/jodatime.svg)](https://travis-ci.org/tengattack/jodatime)
[![Coverage Status](https://coveralls.io/repos/github/abelli5/jodatime/badge.svg?branch=master)](https://coveralls.io/github/tengattack/jodatime?branch=master)
[![Go Report Card](http://goreportcard.com/badge/abelli5/jodatime)](http:/goreportcard.com/report/tengattack/jodatime)

A [Go](https://golang.org/)'s `time.Parse` and `time.Format` replacement supports [joda time](http://joda-time.sourceforge.net/apidocs/org/joda/time/format/DateTimeFormat.html) format.

## Introduction

Golang developers refuse to support arbitrary format of fractional seconds:
[#27746](https://github.com/golang/go/issues/27746), [#26002](https://github.com/golang/go/issues/26002), [#6189](https://github.com/golang/go/issues/6189)

So, we can use this package to parse those fractional seconds not in standard format.

This project is forked from [!(http://github.com//tengattack/jodatime)](http://github.com//tengattack/jodatime). Some methods are appended to mimic joda-time.
## Usage

```go
package main

import (
	"fmt"
	"time"

	"github.com/abelli5/jodatime"
)

func main() {
	date := jodatime.Format(time.Now(), "YYYY.MM.dd")
	fmt.Println(date)
	
    dateTime, _ := jodatime.Parse("YYYY-MM-dd HH:mm:ss,SSS", "2018-09-19 19:50:26,208")
    fmt.Println(dateTime.String())
    
    // add year/month/... and return copy of the instance
    // 增加年月日等字段的值，并返回新实例 
    jt := jodatime.DateHour(2024, 1, 8, 6).AddYear(5).AddMonth(3).AddDay(-6).AddHour(7)
    fmt.Println(jt)

    // set with-year/month/... and return copy of the instance
    // 设置日期字段并返回新实例
	jt = jodatime.DateFull(2021, 3, 4, 5, 6, 7, 8).WithYear(2020).WithMonth(2).WithDay(3).WithHour(4).WithMinute(5).WithSecond(6).WithNanosecond(0)
	fmt.Println(jt)

}
```

## Format

[http://joda-time.sourceforge.net/apidocs/org/joda/time/format/DateTimeFormat.html](http://joda-time.sourceforge.net/apidocs/org/joda/time/format/DateTimeFormat.html)

## License

MIT
