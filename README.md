Paginater [![Build Status](https://drone.io/github.com/Unknwon/paginater/status.png)](https://drone.io/github.com/Unknwon/paginater/latest) [![](http://gocover.io/_badge/github.com/Unknwon/paginater)](http://gocover.io/github.com/Unknwon/paginater)
=========

Package paginater is a helper module for custom pagination calculation.

## Installation

	go get github.com/Unknwon/paginater

## Getting Started

The following code shows an example of how to use paginater:

```go
package main

import "github.com/Unknwon/paginater"

func main() {
	// Arguments:
	// - Total number of rows
	// - Number of rows in one page
	// - Current page number 
	// - Number of page links
	p := paginater.New(45, 10, 3, 3)
	
	// Then use p as a template object named "Page" in "demo.html"
	// ...
}
```

`demo.html`

```html
{{if not .Page.IsFirst}}[First]{{end}}
{{if .Page.HasPrevious}}[Previous]{{end}}

{{range .Page.Pages}}
	{{if eq .Num -1}}
	...
	{{else}}
	{{.Num}}{{if .IsCurrent}}(current){{end}}
	{{end}}
{{end}}

{{if .Page.HasNext}}[Next]{{end}}
{{if not .Page.IsLast}}[Last]{{end}}
```

Possible output:

```
[First] [Previous] ... 2 3(current) 4 ... [Next] [Last]
```

As you may guess, if the `Page` value is `-1`, you should print `...` in the HTML as common practice.

## Getting Help

- [API Documentation](https://gowalker.org/github.com/Unknwon/paginater)
- [File An Issue](https://github.com/Unknwon/paginater/issues/new)

## License

This project is under Apache v2 License. See the [LICENSE](LICENSE) file for the full license text.