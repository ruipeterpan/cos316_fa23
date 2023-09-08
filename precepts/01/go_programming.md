# COS 316 Precepts

# 1. Go Programming

## Variables

- Can you declare multiple variables with different types on the same line?
    
    Yes if you do `var e, f = -1, "lmao"`
    
- Can you infer the types of variables when declaring more than one on a line?
    
    Yes
    
- What does fmt.Println() print when it's given multiple arguments?
    
    Each argument separated by “, ” and a “\n” at the end.
    

## Loops

- Does the scoping of the index variable in a Go 'for' loop extend beyond the loop?
    
    The scope of the index variable in a Go **`for`** loop is limited to the loop's block, and it is not accessible outside of that block.
    
- Can you skip the conditional part in a 'for' loop but still use the init and post statements?
    
    ```python
    package main
    
    import "fmt"
    
    func main() {
    	for i := 0; ; i++ {
    		fmt.Println(i)
    		break
    	}
    }
    ```
    
- Does Go support 'labeled breaks' that let you choose which loop to leave?
    
    Yes, Go supports labeled breaks. Example:
    
    ```python
    package main
    
    import "fmt"
    
    func main() {
        outerLoop:
        for i := 0; i < 3; i++ {
            fmt.Printf("i = %d\n", i)
            
            // innerLoop:
            for j := 0; j < 3; j++ {
                fmt.Printf("j = %d\n", j)
                
                if i == 1 && j == 1 {
                    break outerLoop // This breaks out of the outer loop
                }
            }
        }
    }
    ```
    

## Functions

- Does Go allow you to use '_' to ignore all the return values of a function?
    
    No: `no new variables on left side of :=`
    
- Can you use recursion with a function that returns multiple values?
    
    Yes, here’s an example:
    
    ```python
    package main
    
    import "fmt"
    
    func factorial(n int) (int, int) {
        if n == 0 {
            return 1, 1
        }
    
        prevFactorial, prevResult := factorial(n - 1)
        currentFactorial := n * prevFactorial
        currentResult := n + prevResult
    
        return currentFactorial, currentResult
    }
    
    func main() {
        n := 5
        factorialValue, sum := factorial(n)
        fmt.Printf("Factorial of %d is %d\n", n, factorialValue)
        fmt.Printf("Sum of numbers from 1 to %d is %d\n", n, sum)
    }
    ```
    
- Does Go require a return value for each function?
    
    No. For example,
    
    ```python
    func greet(name string) {
        fmt.Println("Hello, " + name + "!")
    }
    ```