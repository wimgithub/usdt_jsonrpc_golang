# usdtapi

Implement a simple omni core RPC interface.
Support for http basic auth.
Used to help with USDT transfers and monitor address-accounting records.

Examples:

```golang
package main

import (
	"github.com/AdwindOne/usdt"
	"github.com/AdwindOne/usdt/rpc"
	"log"
)

var (
	connCfg = &rpc.ConnConfig{
		Host: "localhost:19031",
		User: "admin",
		Pass: "123456",
	}
)

func main() {
	omni := usdtapi.NewOmniClient(connCfg)

	b, r := omni.GetBalance("mveUkR2wkxL1fVPaD7APMXwbDxbE57yDWC", 3)
	log.Printf("%s, %s\n", b, r)

	h := omni.Send("mveUkR2wkxL1fVPaD7APMXwbDxbE57yDWC", "mpF14fMrBJ3kLAePfHMC3Nppi2wdTZiTiq", 3, "1")
	log.Printf("%v\n", h)

	tx := omni.ListTransactions()
	log.Printf("%v\n", tx)
}
```