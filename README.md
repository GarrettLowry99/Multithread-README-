# Creating Multiple Threads in C#

Use multiple threads when independent work needs to run concurrently. In most C# applications, prefer `Task` and the task-based asynchronous pattern; use `Thread` when you specifically need direct control over a dedicated thread.

## Using `Thread`

1. Define the work each thread will perform.
2. Create a `Thread` for each independent piece of work.
3. Call `Start()` on each thread to begin execution.
4. Call `Join()` when the current thread must wait for them to finish.
5. Handle errors and cancellation as part of the work being performed.

## Shared data

If multiple threads access or change the same data, protect that access with synchronization such as `lock` or a suitable type from `System.Threading`. Avoid holding locks longer than necessary, and never assume threads will run in a particular order.

## Best practices

- Prefer `Task` for most concurrent application work; use `Task.Run` for CPU-bound work and `async`/`await` for asynchronous I/O.
- Avoid creating an unbounded number of threads. For many independent operations, use the task pool or a bounded parallel workflow.
- Keep each unit of work independent where possible.
- Use cancellation and wait for work to finish before the application exits.
