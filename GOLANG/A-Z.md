### Toipcs :
* [Why Go Is Faster](#why-go-is-faster-when-compared-to-other-languages-)
* Interface
* [Struct](#struct)
* [For Loop](#for-loop) [ No while Loop handled in the For loop itself , while , infine loop ]
* [Functions](#functions) *[Anonymus Function , Normal Function , Error Handling Function with Params]*
* Packages [ Public , Private ] Use the Github as The packages if Public use Functon/ Methods Name in Caps private Use in Small
* Polymorphims
* [Go routins](#go-routins) [ If you use the go Key word it will run as GoRoutins ]
*  [Channels](#Channels)
* [Methods](#methods)
*  [MethodVsFunction](#methodvsfunction)
*  [Shortcut](#shortcut)
*  [Error Handling](#error-handling)
*  [Make](#make)
*  [SSEvsWebsockets](#SSEvsWebsockets)
 
### Notes  
 
 
- Go is a Static typed language. [Cant reassign variable once it is declared ]
- Faster than Python.
- By default Go is Async
- Go is for the Devops and Cloud
- concurency Means Excuting Multiple Task At the Same Task Simantaniously by utilizing All available resources more effectively.
- Goroutins for the Concurencys
- iota [ auto increment of values like enumarate keyword in python.]
- IF you want to skip the values use _ to make it as a optional.
- Go key word is used to call the concurency [ Concurrency [Threading in python]  in the python instead of async await ]
- In go There is No Try catch and Final
- No inheritance also
- We can Elimnate Var key word by using the warulas operator inside a Method Alone is Allowed..[important]
- by default the Go will assign the String.
- The main() function itself runs inside its own goroutine, which is automatically created by the Go runtime when your program starts
 
- If you have created the struct and update the Value in the struct and Methods means use pointers to update the value of the Struct due to the performance
variable Types :
Syntax var [keyword] VarName [VariableName] VarType [int/float/etc..]
 
- ``` go mod init <module Name >``` [like npm init or package.json]  vs ``` go mod tidy``` [ it will remove the unused dependncy and packages etc..]
 
 
 - Variadic Functions  [ IN js it is a Spread operator]
 - ### DB
 - Upsert [ At the same time update and insert ]
 - preload [ Joins  , egar load and Lazy loads ]
 - db.raw( "SQL Query capble to Excute it.")
 - db.AutoMigrate () Follwed by the Order What you have Given the Order....
# Backend  API
- By default, GORM pluralizes struct names. Your struct is Reservation, so GORM will create a table named reservations (lowercase, plural).
- By default Go will Take Place the Value for the CreatedAT and UpdatedAT values Not Mandatory option will Seeding..
- (S *UserService) Means You are using the pointer to Modify the Struct  and Instead of  Making a Copy directly Modifying it..
- Zap is a fast, structured, leveled logging library for the Go programming language developed by Uber
- Method recevier
- ```go  print("This will print like in python in go)```
- Context : Used to Carray the Request Related Information Accros the Function calls.  
- ### TEST CASE
- python [MagicMock] in go [Gomock]
 
Flow :
- repo -Test suite while creating the Struct it will inherit it, [ Test Suite life cycle ] [ Sql Mock for the DB ] General Mock for testing it. [ Mock gen ]
 
- service -[depends on the mockgen created by the repo [mockgenrepo] ]  mock invoke the contractor , Table driven cases  
- handler -[depends on the mockgen created by the service [mockgenservice]]  Checking the API Struct is in a valid formate by  
```go
var dk str = "Sample"
 
```
---
 
### Type Conversion :
- By default Go doesnot Support the Implict Type Convertion.
- Expilict Type Conversion is possible..
- Example  :
 
  ```go  
  var x int = 42
  var y float64 = float64(x) // Explicit conversion
  ```
 
- IN go There is No Straight Converstion for the String To Int Using the Package [strconv] Only possible.
- String to Int: strconv.Atoi()
- Int to String: strconv.Itoa()
- Example :
 
  ```go
  package main
 
    import (
        "fmt"
        "strconv"
    )
 
    func main() {
 
        // String to Int
        num, err := strconv.Atoi("100") // Remember Alpabet to In  [Atoi]
        if err != nil {
            fmt.Println("Error:", err)
        }
        fmt.Println("Converted Int:", num)
 
        // Int to String
        str := strconv.Itoa(45)
        fmt.Println("Converted String:", str)
    }
 
    //Output :
    //Converted Int: 100
    //Converted String: 45
 
  ```
 
---
### Why Go is Faster When Compared to Other Languages ?
* In python/java When you Run the program you will be Either Compile / Interupt it.
* To convert the High level language to Low level language for the CPU [0,1] to run the program.
* It is called Translations.
* In go It is directly converted to the Binarys .
* This is by When you Run the Go program it will run a build and Then it convert to the [0,1]
* This is how the Go is Faster when compared to Other languages.
* Unlike Other Languages Garbage Collector it will run we have to Stop the program Exuction and Then we have run it In go It is Performed in a Concurrent Manner in a Milliseconds..
 
---
### Struct:
*What is Struct?*
  - Go is a user-defined type that allows you to group together fields of different data types into a single named entit
  - Custom Types: Allows you to create your own complex data types.
  - Heterogeneous Fields: Unlike arrays or slices, the fields inside a struct can be of completely different data types.
 
*Why we want Struct?*
    Structs bundle related data into clean, manageable types instead of using messy independent variables.
 
    #### 1. Data Grouping
    * Prevents loose, desynchronized variables.
    * Packages attributes into a single object.
    * **Example**: `user1 := User{"Alice", 30}` instead of `user1Name` and `user1Age`.
 
    #### 2. Real-World Modeling
    * Mirrors business logic in your code.
    * Creates highly readable custom types.
    * **Example**: Mapping shapes (`Rectangle`), items (`Product`), or settings (`DatabaseConfig`).
 
    #### 3. API Communication
    * Acts as blueprints for network traffic.
    * Maps JSON keys directly to Go data fields.
    * Uses struct tags like ``json:"direction"`` for seamless translation.
*Why we need Struct?*
    Structs transform scattered variables into reliable, high-performance data blueprints.
 
    #### 1. Code Readability
    * Simplifies long function signatures.
    * Packages multiple arguments cleanly.
    * **Example**: Passing `addr Address` instead of 4 separate strings.
 
    #### 2. Data Standardization
    * Enforces structural contracts across codebases.
    * Guarantees every object shares identical fields.
    * Prevents bugs from missing or inconsistent attributes.
 
    #### 3. Memory Efficiency
    * Allocates data fields sequentially in memory.
    * Maximizes CPU cache efficiency during processing.
    * Outperforms loose, scattered variables in speed.
 
    #### 4. Behavior Attachment
    * Binds functions (methods) directly to data.
    * Enables Object-Oriented patterns in Go.
    * **Example**: Attaching an `AddFunds` action to a `Wallet`.
 
    #### 5. Clean Collections
    * Simplifies managing lists of complex data.
    * Groups mixed data types into uniform slices.
    * **Example**: Creating a slice of `Product` items easily.
 
* Technical Purpose: Memory Allocation and State Management.
* In Go, functions cannot hold data across separate calls. A struct allocates a block of memory to store pointer references to your dependencies (userRepo and logger).
---
 
### For Loop
Go uniquely uses the `for` keyword for all looping structures.
 
#### 1. Standard Loop (C-Style)
Best for counting or running a specific number of times.
```go
for i := 0; i < 5; i++ {
    // Runs 5 times (0 to 4)
}
```
 
#### 2. While Loop (Condition Only)
Go lacks a `while` keyword; pass a single condition to `for`.
```go
for condition {
    // Runs while condition is true
}
```
 
*Example Code*
```go
count := 1
 
for count <= 3 {
    fmt.Println(count)
    count++ // Increments to eventually break the loop
}
```
 
#### 3. Infinite Loop
Go lacks `while(true)`; leave the condition completely blank.
```go
for {
    // Runs forever until a 'break' is hit
    // print("HI")
}
```
 
#### 4. For-Range Loop (Foreach)
 
* Iterates over collections like slices, arrays, maps, and strings.
 
* **Slices/Arrays**: Returns index and value.
  ```go
  for idx, val := range mySlice { }
  ```
* **Maps**: Returns key and value.
  ```go
  for key, val := range myMap { }
  ```
* **Ignore Index/Key**: Use the blank identifier `_`.
  ```go
  for _, val := range mySlice { }
  ```
*Example code*
```go
// Slice/Array Example
nums := []string{"Go", "Rust"}
for idx, val := range nums {
    fmt.Printf("Index: %d, Value: %s\n", idx, val)
}
 
// Map Example
ages := map[string]int{"Alice": 25}
for key, val := range ages {
    fmt.Printf("Key: %s, Value: %d\n", key, val)
}
 
// Ignore Index Example
for _, val := range nums {
    fmt.Println("Value only:", val)
}
```
 
#### 5. Control Keywords
* `break`: Exits the loop immediately.
* `continue`: Skips the current cycle and moves to the next turn.
 
[▲ Back to Topics](#toipcs-)
 
 
---
### Error Handling:
* PANIC
* DEFER
* RECOVER
  *Memory Trick*
    - Try    => [NIL]
    - Except => Recover
    - Finally => Defer
    - Raise   => Panic
 
- *Example*
  ```go
  package main
 
    import "fmt"
 
    func main() {
        // ( 1 ) Set up the safety net FIRST.
        defer func() {
            // ( 3 ) The program crashed! recover() wakes up and catches it.
            // You must explicitly check if err is not equal to nil (!= nil) to turn it into a true/false condition.
            if err := recover(); err != nil {
                fmt.Println("Caught the crash! Error message was:", err)
            }
        }()
 
        fmt.Println("Starting...")
 
        // ( 2 ) BOOM! The program crashes here.
        // It stops everything and jumps straight to the defer safety net above.
        panic("Oh no, something broke!")
 
        fmt.Println("This line is skipped completely.")
    }
 
  ```
 
---
### Make:
 
In Go, make is a built-in function used exclusively to initialize and allocate memory for three specific reference types: slices, maps, and channels.
 
---
 
 
### Why go mod tidy  ???
- It will remove the unused Packages and imports and Add it to the go.mod
 
### Go.mod vs Go.sum :
 
 
| Feature | `go.mod` | `go.sum` |
| :--- | :--- | :--- |
| **Main Function** | Defines module path and dependency requirements. | Lists expected cryptographic hashes of dependencies. |
| **Dependency Definition** | **Yes** (States direct and indirect modules). | No (Only records hashes for verification). |
| **Dependency Verification** | No (Relies on `go.sum` for safety). | **Yes** (Ensures downloaded code has not changed). |
| **File Type** | Configuration Manifest | Cryptographic Lockfile |
| **Human Readable** | **Yes** | No (Mostly hashes and version strings) |
| **Git Versioned** | **Yes** (Commit to repo) | **Yes** (Commit to repo) |
----
 
### Go routins
### Level Set for the Go Routins
  *   **The `go` Keyword**: Start any function as a goroutine by simply typing `go` before the call.
  *   **Lightweight**: They start with only ~2KB of memory, allowing you to run millions at once.
  *   **Managed by Go**: The Go runtime handles the scheduling, not the OS, making context switching extremely fast.
  *   **Main Goroutine**: If the `main()` function finishes, all other goroutines are killed instantly.
  *   **Channels & Sync**: Use **Channels** to share data and **WaitGroups** to ensure the program waits for them to finish.
 
 
* Threading    -> Threading the Method or Tool
  * Example : It will Split the Work in to a Smaller [Thread]
    * Concurrency
    * Parallelism.
  * How you Create Workers
* Concurrency  -> Excuting Multiple Task At the Same Time
  * Example : You Itself Cook Briyani , Chicken 65 , etc..
* parallism    -> Every thing happens AT the same Time.
  * Example  : Each dish Each people will there
  * Exampple : Each Task Each Core Will be Used.
 
 
## *To Keep it In Simple* :
  * Threading: Splitting work into threads that can run independently.
  * Concurrency: Multiple tasks in progress together, not necessarily at the same instant.
  * Parallelism: Multiple tasks executing simultaneously on separate cores.
 
## *Code Example* :
 
```go
package main
 
import (
    "fmt"
    "time"
)
 
func Test (){
    print("\n This Test Function")
    time.Sleep(2* time.Second)
    print("\n Watter is Boliling......")
}
 
func main(){
    fmt.Print("Hello World")
   
    go Test() // Go routines..  
 
    print("\nThis is from the Main......")
    print("\nMain Has Excuted and Waiting for the Goroutine To Compeleted it....")
    time.Sleep(4* time.Second)
    print("\nLast part ")
 
}
 
```
## *Using WaitGroup for the go routine* :
 
## *Code Example* :
```go
package main
 
import (
    "fmt"
    "sync"
)
 
 
func main(){
    fmt.Print("Hello World")
    var wg sync.WaitGroup
    wg.Add(1)
    go func ()  {  // It  an anonymous goroutine
        defer wg.Done()
        sample()
       
    } () // You Must decleare the () Other wise it will through an Error Expression Must be a Function call
    wg.Wait()
    print("Wait Untill the Background Goroutine To Compelete it work to Stop the Main Thread...")
}
 
func sample (){
    print("This is a goroutine")
}
```
---
 
### *Channels*
 
## *Why We Need Channels* :
* > Channels in Go are communication pipes between goroutines.
* > With out Channels Cause race Condtions , Multiple Goroutines Access the Same Variable.
 
* > *SYNTAX* :
  ```go  
  ch:= make(chan int)
  ```
 
```go
  // Unbuffered channel (Blocks instantly until someone reads)
ch := make(chan int)
// Buffered channel (Holds 3 items before blocking)
ch := make(chan int, 3)
 
```
* > *SYNTAX* :
 
```go
  // SEND data into a channel (Arrow points INTO the channel)
ch <- 42
 
// RECEIVE data from a channel (Arrow points AWAY from the channel)
value := <-ch
 
// CLOSE a channel (Tells receivers no more data is coming)
close(ch)
 
```
 
```go
 
package main
 
import (
    "fmt"
)
 
 
func main(){
    fmt.Println("Hello World")
    ch := make (chan string , 2)
    ch <- "Test-1"
    ch <- "Test -2"
    close(ch)
 
    for val := range ch {
        fmt.Println("The Value is --->", val)
    }
 
    Value , isOpen := <-ch
    fmt.Println("The Value is ", Value)
    fmt.Println("The Channel is Alive or Not..",isOpen)
}
 
// PS C:\Users\Dharaneedhar_xs89l8a\Documents\GO\Samples> go run sample.go
// Hello World
// The Value is ---> Test-1
// The Value is ---> Test -2
// The Value is  // Empty Value.
// The Channel is Alive or Not.. false
// PS C:\Users\Dharaneedhar_xs89l8a\Documents\GO\Samples>
 
```
## Name Channels
 
```go
package main
 
import "fmt"
 
func main() {
    // Name your channels like real-world objects!
    userEmailChannel := make(chan string)
    orderIdChannel   := make(chan int, 5) // Buffered
 
    // Using the named channels
    go func() {
        userEmailChannel <- "user@example.com"
        orderIdChannel <- 98765
    }()
 
    // Reading from the named channels
    email := <-userEmailChannel
    order  := <-orderIdChannel
 
    fmt.Println("Sending email to:", email)
    fmt.Println("Processing order #:", order)
}
 
// or
 
package main
 
import "fmt"
 
func main() {
    // Name your channels like real-world objects!
    userEmailChannel := make(chan string)
    orderIdChannel   := make(chan int, 5) // Buffered
 
    // Using the named channels
    go func() {
        userEmailChannel <- "user@example.com"
        orderIdChannel <- 98765
        orderIdChannel <- 98761
        orderIdChannel <- 98762
        orderIdChannel <- 98763
        orderIdChannel <- 98764
    }()
 
    // Reading from the named channels
    email := <-userEmailChannel
    order  := <-orderIdChannel
    order1  := <-orderIdChannel
    order2  := <-orderIdChannel
    order3  := <-orderIdChannel
    order4  := <-orderIdChannel
 
    fmt.Println("Sending email to:", email)
    fmt.Println("Processing order #:", order)
    fmt.Println("Processing order #:", order1)
    fmt.Println("Processing order #:", order2)
    fmt.Println("Processing order #:", order3)
    fmt.Println("Processing order #:", order4)
}
 
// Output :
// Sending email to: user@example.com
// Processing order #: 98765
// Processing order #: 98761
// Processing order #: 98762
// Processing order #: 98763
// Processing order #: 98764
 
```
 
### Select Statement in the Channels :
```go
package main
 
import (
    "fmt"
    "time"
)
 
func main() {
    uberEatsChannel := make(chan string)
    swiggyChannel   := make(chan string)
 
    // Background Worker 1: UberEats takes 2 seconds to get ready
    go func() {
        time.Sleep(2 * time.Second)
        uberEatsChannel <- "🍔 Pizza from UberEats has arrived!"
    }()
 
    // Background Worker 2: Swiggy takes 1 second to get ready
    go func() {
        time.Sleep(1 * time.Second)
        swiggyChannel <- "🍛 Biryani from Swiggy has arrived!"
    }()
 
    // The Switchboard: Listen to both channels at the exact same time
    select {
    case foodFromUber := <-uberEatsChannel:
        fmt.Println("Eating:", foodFromUber)
 
    case foodFromSwiggy := <-swiggyChannel:
        fmt.Println("Eating:", foodFromSwiggy) // This will run first!
    }
}
 
```
 
 
 
*   **Passing Data**: One worker (goroutine) creates a result and "hands it off" to another worker safely through the channel.
*   **Coordination (The Wait)**: Channels act like a signal. One goroutine can stop and wait for a "Go!" signal from another.
- Two Type of Channels :
  1) Buffered  [It acts like a queue. You can send data into it and keep going, even if no one is there to pick it up yet.] :
      - Size :  A channel with a fixed capacity (make(chan int, 5))
 
  2) Unbuffered [It requires a "handshake." The sender and receiver must meet at the exact same time.]
       - Size : A channel with zero capacity (make(chan int)).
 
* 1. Creating Basic (Unbuffered) Channels
* 2. Creating Buffered Channels
* 3. Directional Channels
 
# Buffered VS Un Buffered  Defining the Size . Capacity...
- No capacity UnBuffered.
- Define the Capacity.
- Channels Capable of Sending Any datatype
- Size of the Channels.
> Buffered Go Routine is Not Mandatory As We are defining the Size IN Unbuffured Needes the GoRoutine if we wont use it same thread itself act as a Sender and reciver.
 
### *Notes Over Channels*
* Order of receiving and sending data is Consistent in channels thought the FIFO [Queue]
###
```go
```
 
 
### Functions
 
- We can give the name for the return type
 
*Optional Parameter*
```go
// - Optioanl parameter Use the _
 
package main
import "fmt"
 
func add(a int , _ int )  (int) {
    return a
}
func main() {
 print("The result " , add(3,2))
}
```
*Normal Function*
```go
//  This is a Normal Function in go
package main
import "fmt"
 
func add(a int , b int )  (c int) {
    return a + b
}
func main() {
//   fmt.Print("The result " , add(3,2))
 print("The result " , add(3,2))
}
```
 
*Returning a Varible as the return Type*
```go
//  Assigning the variable to the return type and getting the Value
 
package main
import "fmt"
 
func add(a int , b int )  (c int) {
    c = a + b
    return
}
func main() {
//   fmt.Print("The result " , add(3,2))
 print("The result " , add(3,2))
}
```
 
```go
//  Taking the optional Parameters and always returning only the constant Value as a Output..
 
package main
 
import "fmt"
func add( int , int )  ( int) {
    return 0
}
func main() {
//   fmt.Print("The result " , add(3,2))
 print("The result " , add(3,2))
}
 
// Output :  The result 0
 
```
 
---
[▲ Back to Table of Contents](#toipcs-)
 
### DEFER Method
- Act like a Finally Block in other languages..
```go
//  Simple Example...
package main
 
func Sample() {
    defer print("This is a defer....")
    print("This is a Sample")
}
func main() {
    Sample()
   
}
 
// Output :
// This is a Sample
// This is a defer....
```
- We can Use the DEFER AS a Anynomous Functions also
```go
 //  Simple Example...
package main
 
func Sample() {
    defer func() {
        print("\nThis is a defer....")
    }()   // Here () is a Mandatory For the Annomous Function..... For the defer..
    print("This is a Sample")
}
func main() {
    Sample()
   
}
```
 
---
 
 
### Methods
 
* Method is simply a function that has a special receiver argument.
* This receiver binds the function to a specific type (like a struct), allowing you to call the function using "dot notation" (e.g., object.MethodName()).
 
#### Syntax Layout
Place the receiver parameter in its own parentheses before the function name [1]:
 
```go
func (receiverName ReceiverType[StructName]) MethodName(parameters) returnTypes {
    // method body
}
```
 
*Example Code Block*
 
```go
package main
 
import "fmt"
 
// 1. Define a struct type
type Rectangle struct {
    Width  float64
    Height float64
}
 
// 2. Define a method with a Rectangle receiver
func (r Rectangle) Area() float64 {
    return r.Width * r.Height
}
 
func main() {
    // 3. Create an instance of the struct
    rect := Rectangle{Width: 10, Height: 5}
 
    // 4. Call the method using dot notation
    fmt.Println("Area:", rect.Area()) // Output: Area: 50
}
 
 
 
```
 
### Value Receivers vs. Pointer Receivers
 
Go methods accept two types of receivers. Choosing the correct one impacts data mutation and performance.
 
#### 1. Value Receiver `(r Rectangle)`
* **How it works**: Passes a **copy** of the data to the method.
* **Use case**: Reading data without modifying the original object, or for small, simple types.
 
#### 2. Pointer Receiver `(r *Rectangle)`
* **How it works**: Passes the **memory address** of the original object.
* **Use cases**:
  * Modifying or mutating the actual fields of the receiver.
  * Optimising performance for large structs to avoid memory copying overhead.
 
[▲ Back to Topics](#toipcs-)
 
---
### MethodvsFunction
 
1) Function :
   - A function is an independent block of code. You call it directly by its name and pass any necessary data as arguments.
```go
func Add(a int, b int) int {
    return a + b
}
 
// Called like this:
result := Add(5, 10)
 
```
1) Method :
   - A method is a function that is "attached" to a specific type (like a struct). It has a receiver—an extra parameter listed before the function name that gives the method access to the data inside that type.
 
 
```go
type Circle struct {
    Radius float64
}
 
// (c Circle) is the receiver
func (c Circle) Area() float64 {
    return 3.14 * c.Radius * c.Radius
}
 
// Called like this:
myCircle := Circle{Radius: 5}
result := myCircle.Area()
 
```
 
### Shortcut
 
- fp => fmt.Println("")
- To get the type like in python [type(a)] here  fmt.Println("%T", variable)
 
 
 
 
### WEB SHOCKTS :
- Use When We Want the Live communications
- No headers [ No Auth is possible ,
- To resolve it i will get it as get request if it is a valid request then it will send the in ws protocol[101] ]
- webscoket protocol is 101
- WebScoket TCP Communication.
- pub sub
- hub
- broradcast
- global array
- reduce or Close the connection.
- Marshal and Unmarshal   [ unmarshal means decoding serialized data (like JSON, XML, or binary) and converting it back into a Go-native data structure (like a struct, map, or slice)] [ Like python Loads and Dumps ]
- IF Connection is disconnected , but not closed , the array will go increase it.
- PING PONG [HeartBeat] [ To Test The Avalability of the Websocket...]
- To Save Means To Be Saved in Cache for the Future Use...
-
# UseCase
 - Gaming
 - Stock Market
 - Colabrative WOrking
 - Live Location Tracking
 - Teams , WhatsApp , Slack Communication through the Websocket.. Example [ In whats app group show 500 people are in the Online.. ]
 
 
---
### SSEvsWebsockets
*What is SSE?*
* Server-Sent Events is a technology that allows a web server to push continuous, real-time updates to a browser or client over a standard HTTP Connections
*Differnces*
* **Data Flow**: SSE is strictly unidirectional (server-to-client). WebSockets are bidirectional.
* **Protocol**: SSE runs over standard HTTP/HTTPS. WebSockets use a dedicated WS/WSS protocol.
* **Data Format**: SSE sends text only (UTF-8). WebSockets can send both text and binary data.
* **Connection Limit**: SSE is limited to 6 connections per domain under HTTP/1.1 (lifted under HTTP/2). WebSockets have no browser limit.
---
 
 
 
### Memory  :
 
 
 - *Esacape Analysis*: varaible is Assign Means it will to the Stack  , if the Varible is refernced by the pointer and refernced Means it will go the Heap.
 - To Find this Heap or Stack We Use this ```go go build-gcflags="-m" ```
 - In  concurrency Heap is Shared Between the Goroutines and Stack is private per Goroutines...
 - *Garbage Collector Log*
- GC Works By the Mark and Sweep Algo. [ It will mark the varibles that Still in Use.] [ Sweep Remove Every thing Not Marked]
Syntax :
 
```go  
$env:GODEBUG="gctrace=1"; go run sample.go
```
```go
gc 1 @0.034s 1%: 0+4.7+1.9 ms clock, 0+1.0/1.0/0+15 ms cpu, 3->4->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 2 @0.051s 1%: 0+1.4+0.32 ms clock, 0+0/0.93/0.93+2.6 ms cpu, 3->3->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 3 @0.079s 1%: 0+1.0+0 ms clock, 0+1.0/2.0/0+0 ms cpu, 3->3->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 4 @0.101s 1%: 0+1.0+0 ms clock, 0+0/0.54/1.0+0 ms cpu, 3->3->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 5 @0.119s 1%: 0+1.0+0 ms clock, 0+0/1.6/0.53+0 ms cpu, 3->3->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 6 @0.147s 1%: 0+1.0+0 ms clock, 0+0/2.0/2.0+0 ms cpu, 3->3->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 7 @0.169s 1%: 0+1.2+0 ms clock, 0+0/1.1/1.6+0 ms cpu, 3->3->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 8 @0.191s 1%: 0+0.53+0 ms clock, 0+0/1.0/0+0 ms cpu, 3->3->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 9 @0.205s 1%: 0+1.5+0 ms clock, 0+0/1.9/0.99+0 ms cpu, 3->3->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 10 @0.255s 1%: 0+3.0+0.43 ms clock, 0+1.6/1.0/0+3.5 ms cpu, 3->4->2 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 11 @0.263s 1%: 0.56+1.2+0 ms clock, 4.5+0.52/2.4/1.0+0 ms cpu, 3->4->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 12 @0.298s 1%: 0.51+1.5+0 ms clock, 4.1+0/1.6/0.66+0 ms cpu, 3->3->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 13 @0.307s 1%: 0+1.2+0 ms clock, 0+0/1.8/0+0 ms cpu, 3->4->2 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 14 @0.314s 1%: 0+1.9+0 ms clock, 0+0/2.9/0+0 ms cpu, 3->4->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 15 @0.326s 1%: 0+1.1+0 ms clock, 0+0/1.7/0.59+0 ms cpu, 3->3->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 16 @0.334s 1%: 0+1.1+0 ms clock, 0+0.55/1.1/0+0 ms cpu, 3->3->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 17 @0.354s 1%: 0+1.8+0 ms clock, 0+0/2.9/3.2+0 ms cpu, 3->3->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 18 @0.362s 1%: 0+1.0+0 ms clock, 0+0/2.1/2.0+0 ms cpu, 3->3->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 19 @0.372s 1%: 1.0+0.99+0 ms clock, 8.0+0/0/0+0 ms cpu, 3->4->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 20 @0.380s 1%: 0+2.0+0 ms clock, 0+0/2.0/1.0+0 ms cpu, 3->3->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 21 @0.392s 1%: 0+1.0+0 ms clock, 0+0/1.0/1.0+0 ms cpu, 3->3->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
gc 22 @0.412s 2%: 0.51+1.0+0 ms clock, 4.1+0/1.0/1.0+0 ms cpu, 3->3->1 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
 
Hello World
This is a goroutine
Wait Untill the Background Goroutine To Compelete it work to Stop the Main Thread...
PS C:\Users\Dharaneedhar_xs89l8a\Documents\GO\Samples>
```
 
----
 
[▲ Back to Topics](#toipcs-)