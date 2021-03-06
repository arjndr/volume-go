# volume-go [![Travis Build Status](https://travis-ci.org/itchyny/volume-go.svg?branch=master)](https://travis-ci.org/itchyny/volume-go) [![Go Report Card](https://goreportcard.com/badge/github.com/itchyny/volume-go)](https://goreportcard.com/report/github.com/itchyny/volume-go) [![MIT License](http://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/itchyny/volume-go/blob/master/LICENSE) [![GoDoc](https://godoc.org/github.com/itchyny/volume-go?status.svg)](https://godoc.org/github.com/itchyny/volume-go)
### Volume control in Go
This is a Go language package for controlling audio volume.

## CLI tool usage

#### install

```sh
 $ go get -u github.com/itchyny/volume-go/cmd/volume
```

#### get

Gets current volume.

```sh
 $ volume get 
20
```

#### set

Set volume to specified amount.

```sh
 $ volume set 40
 $ volume status
volume: 40
muted: false
```

#### up/down

Increase/decrease volume by specified amount, default 6.

```sh
 $ volume get
40
 $ volume up
 $ volume get
46

 $ volume up 4
 $ volume get
50

 $ volume down
 $ volume get
44
 $ volume down 4
 $ volume get
40
```

#### status

Get current volume and is muted.

```sh
 $ volume status
volume: 20
muted: false
```

#### mute/unmute

```sh
 $ volume mute
 $ volume status
volume: 20
muted: true

 $ volume unmute
 $ volume status
volume: 20
muted: false
```

## Package usage
```go
package main

import (
	"fmt"
	"log"

	"github.com/itchyny/volume-go"
)

func main() {
	vol, err := volume.GetVolume()
	if err != nil {
		log.Fatalf("get volume failed: %+v", err)
	}
	fmt.Printf("current volume: %d\n", vol)

	err = volume.SetVolume(10)
	if err != nil {
		log.Fatalf("set volume failed: %+v", err)
	}
	fmt.Printf("set volume success\n")

	err = volume.Mute()
	if err != nil {
		log.Fatalf("mute failed: %+v", err)
	}

	err = volume.Unmute()
	if err != nil {
		log.Fatalf("unmute failed: %+v", err)
	}
}
```

## Bug Tracker
Report bug at [Issues・itchyny/volume-go - GitHub](https://github.com/itchyny/volume-go/issues).

## Author
itchyny (https://github.com/itchyny)

## License
This software is released under the MIT License, see LICENSE.
