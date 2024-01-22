# Error Handling 
<pr>Most languages don’t distinguish between recoverable (example: file not found error this might require retry operation) and non-recoverable errors (example: bug like trying to access location beyond the end of the array requires termination of the program) and handle both in the same way, using mechanisms such as exceptions. Rust doesn’t have exceptions. Instead, it has the type `Result<T, E>` for recoverable errors and the `panic!` macro that stops execution when the program encounters an unrecoverable error.</pr> 

### 1. `std::io::Result<()>`
In Rust, `std::io::Result<()>` is a type that represents the result of an I/O operation that could either succeed (`Ok(())`) or fail (`Err`) with an associated error. The `()` inside `Ok(())` is the unit type, and it is used here because I/O operations often don't produce meaningful values, but the focus is on whether the operation succeeded or failed.

Here are the possible outcomes:

1. **Success (Ok(())):** The I/O operation succeeded, and the () inside Ok(()) signifies that there is no meaningful result or data associated with the success.
2. **Failure (Err):** The I/O operation encountered an error, and the Err variant holds an associated value that represents the specific error.

Common error scenarios might include:  
File not found.  
Permission issues.  
Insufficient resources.  
Network errors.  
Invalid input.  
When you see a function returning `std::io::Result<()>`, it means the function is reporting the success or failure of an I/O operation, and if it fails, you can inspect the associated error to understand what went wrong. Here's how.


