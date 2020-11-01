# TAphone

TAphone is a phonetic algorithm for indexing Tamil words by their pronunciation, like Metaphone for English. The algorithm generates three Romanized phonetic keys (hashes) of varying phonetic affinities for a given Tamil word. This package implements the algorithm in Go.

The algorithm takes into account the context sensitivity of sounds, syntactic and phonetic gemination, compounding, modifiers, and other known exceptions to produce Romanized phonetic hashes of increasing phonetic affinity that are very faithful to the pronunciation of the original Tamil word.

- `key0` = a broad phonetic hash comparable to a Metaphone key that doesn't account for hard sounds and phonetic modifiers
- `key1` = is a slightly more inclusive hash that accounts for hard sounds.
- `key2` = highly inclusive and narrow hash that accounts for hard sounds and phonetic modifiers.

### Examples

| Word       | Pronunciation | key0    | key1    | key2      |
| ---------- | ------------- | ------- | ------- | --------- |
| தமிழ் 	|  |  TM3Z |  T1M3Z |  T1M3Z |
| தமிழ்மொழி 	|  |  TM3ZMZ3 |  T1M3ZMZ3 |  T1M3ZM7Z3 |
| பந்து 	|  |  PNT |  PNT1 |  PNT14 |
| பந்தயம் 	|  |  PNTYM |  PNT1YM |  PNT1YM |

### Go implementation

Install the package:
`go get -u github.com/cmrajan/taphone`

```go
package main

import (
	"fmt"

	"github.com/cmrajan/taphone"
)

func main() {
	k := taphone.New()
	fmt.Println(k.Encode("தமிழ்"))
	fmt.Println(k.Encode("வணக்கம்"))
}

```

License: GPLv3


#cors
headers / {
Access-Control-Allow-Origin *
-Server
}