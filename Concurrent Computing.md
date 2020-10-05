# Concurrent Computing

### 1. Introduction and History

**Concurrency** is a property given to systems (e.g. software and/or hardware) in which **multiple sequential processes** are running **simultaneously, interacting** with each other.

A **sequential process** is a unit of sequential execution

### 2. Towards Concurrent Programming in Go

given an input, a single sequential process (=thread) produces a
**single sequence of memory state changes** deriving the output



#### Go

Start new goroutine running the function `say()`

##### Goroutine 

1.  is a green thread(user-space threads——created and managed by the Go runtime, not the OS)(程序里面的线程不会真正映射到操作系统的线程，而是由语言运行平台自身来调度)
2. is an application-level thread
3. is much more lightweight than an OS-thread

In order to run goroutines G, a thread M must hold a context P.![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571594906186.png)

M:N 多个goroutine在多个内核线程上跑

##### Memory

Goroutines run in the same address space, so access to shared memory must be synchronized(同步)

Don't communicate by sharing memory, share memory by communicating.(不要通过分享记忆来交流，要通过交流来分享记忆)

##### Channels

Channel provides a way to send a message between two
goroutines.

`channel := make(chan int)` 	to create a new channel

```go
someInt := 5

channel <- someInt
```

**Send** `someInt` to the channel

`v := <-channel` 	Receive **from** channel and assign the received value to v.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571574494218.png)

`x := <-leftSum`				Receive the results from the two goroutines.
`y := <-rightSum`		

Sends and received **BLOCK** until the other side is ready.

##### Functions

Functions are values can be passed around just like other values.![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571579529722.png)

##### Closures

A closure is a function value that references variables from outside its body. The closure may access and modify the referenced variables.



###### Additional

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571584456436.png)

`package main`	declare that this file belongs to the main package

only `main` packages can have executable `main()`functions.

`"fmt"` short for format

`func` keyword is to declare a function

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571584803008.png)

`:=` declares a new variable

`=` assigns a value to an existing variable

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571583910989.png)

Go allows multiple return values. 

`swap()` takes two strings and returns two strings

```
func swap(x string, y string)(string, string){...}
==
func swap(x, y string) (string, string)

Because of Both x and y are of type string .
```

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571584844174.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571584918565.png)

if declared with the `for` with no boolean condition then that is infinite while loop

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571585418251.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571585457525.png)

```go
type Vertex struct {
	X int
	Y int
}

```

Declare a struct with two fields

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571585581760.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571585617321.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571585634367.png)

Arrays are passed by VALUE![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571585729221.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571585768215.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571585788947.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571585809568.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571585919501.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571585952934.png)

close() closing a channel indicates that no more values will be sent.

[https://gobyexample.com/]()

[https://tour.golang.org/list]()

### 3. Deadlock & Channel Communication

explicit information exchange:

1. shared memory model
2. message passing model

#### Mutual Exclusion Interlude(互斥段)

Principles: a train must never enter the single line section unless it has a token.
The token machines must never allow more than one token out at any time.

#### Data races

it happen when

1.  two or more threads have access to the same data
2. at least one of them is writing to this data
3. there is no synchronization

#### Message Passing

1. processes communicate by sending and receiving messages 
2. transfer of data between processes needs cooperative operations to be performed by each process (e.g. every send operation must have a matching receive) 



**Channels** are an abstraction: they provide a **uniform representation** of communication.

A channel is **lossless** (every data item sent is delivered)

Channels are communication links between two goroutines.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571587946860.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571588396573.png)

Channels are communication links between processes (goroutines, say).

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571588337993.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571588940805.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571592559701.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571592665015.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571595510143.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571595623263.png)

### 5. Sharing Memory, Locks and Critical Sections 

**Critical sections** are code fragments that interact with a shared resource and should not be accessed by more than one thread at any one time.

busy waiting(spinning) : a thread repeatedly checks to see if a condition is true

### 6. Sharing Memory: condition variables and semaphores in C

**Mutex locks：** used to protect critical sections of code - specifically to prevent a race condition

**Condition variables ：**used to put threads to sleep and wake them up again – help to avoid busy waiting

Require an associated predicate

**Semaphores (信号标) :**  can be used to perform different tasks depending on their initial value

semaphore has a value ≥ 0.

**post** — increase the value by 1(auto)

**wait**—if > 0, decrease by 1(auto), otherwise wait until this becomes possible.

wait before entering a critical section, post when you exit it.![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571616120432.png)

**Condition variables :** like semaphores, may be used to suspend threads(挂起线程) without resorting to busy waiting

Threads are suspended until a particular condition is met, when the condition is met they (the threads) are woken up and automatically obtain the mutex lock associated with that condition

Threads should then check if the condition still holds before proceeding into the critical section

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571616277929.png)

### 7. Sharing Memory, Locks Critical Sections, condition variables and semaphores

Lock need to be in critical section so that it will not have data race.![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571735031882.png)

 producer-consumer add while condition, it will be like a alarm that will sleep and when a thread send some thing, it will wake all threads who waiting it. and it will go through while loop again make sure it is right.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1571914684744.png)

### 9. CSP Abstraction: Events, Processes, Trace and Refinement

communication sequential processes(通信顺序进程) :enable a systematic
specification and analysis approach for concurrent

CSP processe: are independent, sequential entities

​						  engage in events(e.g. operations visible to the environment)

​						  may communicate with other processes via common events

​						  are completely described by their possible event sequences

Primitive processes have STOP(communicates nothing - deadlock) and SKIP(terminated successfully - work done)



Events

represent visible behaviors of a process (e.g. communications), which are atomic (indivisible) and instantaneous. 

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572524927658.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572524946531.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572524979629.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572525010604.png)

think  as theory computational 

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572528301933.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572529860738.png)

**Trace :** is a finite sequence of events, representing a particular behaviour of a process up to a point in time.![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572530501583.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572530777104.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572530919934.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572531153308.png)

w.r.t = with regard to 

**Process interaction : **means processes simultaneously perform events

interaction allows to place a process P into an environment of other(concurrently existing) process.

### 10 & 11 CSP: Choice, Refusals, Failures

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572534639908.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572534804113.png)

Example![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572534723038.png)

refusals(P/<a>)  = {...}mean after take a in the process the rest in {} is not available. ![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572535978893.png)

Example 2

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572536048590.png)

Example 3![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572536091175.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572536305039.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572536330245.png)

external choice :  A process that can behave like P or Q, where the choice is made by the environment, is denoted P  □ Q

internal choice : A process that can behave like P or Q, where the choice is made( non-deterministically) by the process itself, is denoted P ∏ Q

### 13-14 CSP : Liveness, Deadlock, Livelock

#### Divergence and hiding![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200203035747933.png)

In CSP, possibility of an infinite sequence of n events is called livelock or divergence.

a divergent process cannot be guaranteed to make any progress.

### 15. Petri Nets

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200203040723603.png)

Firing : When a transition fires (atomic), it consumes all input tokens, and places tokens at the end of all output arcs.

Inhibitor arcs : An inhibitor arc from a place to a transition is used to indicate that token presence at the place disables the linked transition(如果这个state有token了就禁止某个传输)

A Petri net is **k-bounded** (or simply bounded) if the number of tokens in each place does not exceed a finite number k for any marking reachable from a petri net

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200203041844438.png)

Liveness of a Petri Net: An entire Petri net with initial marking M0 is called live if, at any stage it is possible to ultimately fire any transition by progressing through some further firing sequence. A live Petri net guarantees deadlock-freedom, no matter what firing sequence is chosen. (In contrast: A transition is dead if it can never be fired.)