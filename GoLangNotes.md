# Ediors
1. VS Code
1. GoLand

# Hello World

## Code 
```
package main
import "fmt"
func main() { fmt.Println("Hello world") }
```

## Build and Execute
1. go build .\main.go .\deck.go --> Build
1. .\main.exe --> Execute
1. go install github.com/golangci/golangci-lint/cmd/golangci-lint@v1.47.3`. `go build` just compiles the executable file and moves it to the destination. go install does a little bit more. It moves the executable file to $GOPATH/bin
In my laptop, it built and copied build artifact to /Users/datkrish/go

# Basic Language Constructs

## Declare Primitive Variable
1. `var card int = 0`
1. `card := 0`

## Working with Array or List

### Declare Slice
`cards := []string{"item1", "item2"}`
`content := []byte{}` - init empty slice
`content = make([]byte, 99999)` - allocate byte slice of 99999

### Range Syntax
1. array[0:2] selects element at 0, 1.
1. array[2] selects element at 0, 1.
1. array[:2] selects element at 0, 1.
1. array[2:] selects element at 2 till end of array.


## `if` Condition
1. Sample
```
	if err := json.Unmarshal(bytes, &user); err != nil {
		fmt.Println(err)
		return
	}
```

1. Sample
```
	if err != nil {
		fmt.Println(err)
		return
	}
```

## Loop
```
for i, card := range cards {
  fmt.Println(i, card)
}
```

## Receiver
func (d deck) print() {
	for i, card := range d {
		fmt.Println(i, card)
	}
}

## Return two values from function
```
func deal(d deck, handSize int) (deck, deck) {
...
}
```
Assingin them in place where function is called `hand, remainingCards := deal(cards, 5)`

## Type Cast Examples
1. Type cast `d` as slice of string by `[]string(d)`
1. Type cast string as byte slice `[]byte(d.toString())`

## Structure data type in Go
```
type Person struct {
	firstName string
	lastName string
}
// Using struct
func main() {
	alex := person{"Foo", "Bar"}
	fmt.Println(alex)
	alex = person{firstName: "Foo", lastName: "Bar"}
	fmt.Println(alex)
}

```

## Pointers
1. GO is pass by value language
1. `&myname` - gives address of myname.
1. func (ptrMyName *Name) myfunc() {} --> *Name is how pointer can be received by func.
1. Inside function `(*ptrMyName)` gives content of pointer address.
1. There are various methods of calling 
    1. mynamePtr := &myname
    mynamePtr.updateName("NewFirstName1")
    1. (&myname).updateName("NewFirstName2")
    1. myname.updateName("NewFirstName3")

# Unit Testing
1. Initialize module by executing in command line `go mod init deck`
1. Call tests with go file name e.g. `deck_tst.go` , where my logic is in `deck.go`.
1. Execute the test by running command `go test`

# External Dependencies

## How to use external modules
1. Here i am using `github.com/gorilla/mux`, by using 
```
import (
	"github.com/gorilla/mux"
)
```
1. `go mod init deck`
1. `go get github.com/gorilla/mux`. This adds `require github.com/gorilla/mux v1.8.0 // indirect` into `go.mod`.

## HTTP Framework
1. Gin-Gonic is popular HTTP framework. https://github.com/gin-gonic/gin#readme
    `go get -u github.com/gin-gonic/gin`
1. curl examples
    1. `curl localhost:8080/ping -v`
    1. `curl -X POST localhost:8080/users -v`

# Interfaces
## Declare and Implement Own Interfaces
1. `type bot interface {getGreeting() string}` --> this is how interface is declared
1. `func printGreeting(b bot) {fmt.Println(b.getGreeting()) }`  --> this is how method implemented for interface.
1. `printGreeting` can be called for any `bot` that has implementation for `getGreeting`.
1. Interfaces can vary in arguments and return types.

## Implement Interfaces Defined by Others
1. Below example implements Writer interface `Write(bs []byte) (int, error)`
```
type logWriter struct{}
func (logWriter) Write(bs []byte) (int, error) {
	fmt.Println(string(bs))
	fmt.Printf("Just wrote %d many bytes", len(bs))
	return len(bs), nil
}
```

# Concurancy by using Go Routines and Channels
1. Concurancy is not parallelism
1. Running program has main routine, and can trigger child routines. Main and child can exchange message through channels.
1. Function Literal is same as Anonymous method or Lambda method

# Miscellaneous
1. `fmt.Sprintf("Hi %s", "datha")`
1. `panic(err)` - way to exit with error.
1. Package can implement methos called `func init() {...}` to initialize e.g. to connect to db.
1. `os.Getenv("envvarname")` --> collect value from environment variable.
1. `defer stmt.Close()` --> everything deferred will be executed before `return`.

# Database
1. `sql` is the library import. `sql.Open()` 
1. ` "github.com/go-sql-driver/mysql"` --> this is another strange way at import, to instruct to import without using it.
1. `mysql.SetLogger()` --> how logger can be supplied to logger.
1. `Client.Prepare("<SQL query>")` --> prepares sql query for execution. `Close()` must be called when query no longer needed.
1. `Exec()` - execute statement.
1. `strings.Contains()` - check if string has substring.
