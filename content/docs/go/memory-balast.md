---
title: Go memory ballast technique
---

* In go, the GC will trigger every time the heap size doubles.
* If you know your steady state heap size you can “pre-allocate” it by creating a “ballast”.
```go
func main() {
    // Create a large heap allocation of 10 GiB
    ballast := make([]byte, 10<<30)

    // Application execution continues
    // ...
}
```


* If a ballast of 10 GiB is allocated, the next GC will only trigger when the heap size grows to 20 GiB. At that point, there will be roughly 10 GiB of ballast + 10 GiB of other allocations.
* When the GC runs, the ballast will not be swept as garbage since we still hold a reference to it in our main function, and thus it is considered part of the live memory.
* Memory in 'nix systems (and even Windows) is virtually addressed and mapped through page tables by the OS. When the above code runs, the array the ballast slice points to will be allocated in the program’s virtual address space. Only if we attempt to read or write to the slice, will the page fault occur that causes the physical RAM backing the virtual addresses to be allocated.

# References
* https://blog.twitch.tv/en/2019/04/10/go-memory-ballast-how-i-learnt-to-stop-worrying-and-love-the-heap-26c2462549a2/ 