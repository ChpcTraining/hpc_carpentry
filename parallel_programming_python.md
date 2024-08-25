# Intro

## Concurrency vs. Parallelism

### Concurrency:

Definition: Concurrency refers to the ability of a system to handle multiple tasks or processes simultaneously in an overlapping manner. However, these tasks might not be executing at the exact same time.

How it works: In a concurrent system, multiple tasks are in progress at the same time, but they may be interleaved on a single core or processor. For example, while one task is waiting for input/output (I/O), another task might be executed. This gives the illusion of parallelism.

Example: Imagine a single chef preparing multiple dishes. The chef might start chopping vegetables for one dish, then while they are simmering, they start cooking another dish. The chef switches between tasks, but only one task is actively being executed at any moment.

### Parallelism:

Definition: Parallelism is a type of concurrency where multiple tasks are executed simultaneously across multiple cores or processors. Parallelism involves actually running multiple tasks at the same time.

How it works: Parallelism requires multiple processors or cores. Different tasks or parts of a task are assigned to different processors, allowing them to be executed simultaneously.

Example: Imagine having multiple chefs in a kitchen, each preparing a different dish at the same time. Here, multiple tasks (dishes) are truly being executed in parallel.

## Synchronous vs. Asynchronous

### Synchronous:

Definition: In a synchronous process, tasks are executed sequentially, meaning each task must complete before the next one can begin. The tasks are typically executed in a blocking manner, where one task waits for the previous one to finish.

How it works: Synchronous operations are straightforward—each step waits for the previous step to complete. This is often easier to reason about but can be inefficient if a task is idle or waiting for something (like I/O).

Example: A person making breakfast might toast bread, then fry eggs, and finally brew coffee. They wait for the toast to finish before starting the eggs, and then for the eggs to finish before starting the coffee.

### Asynchronous:

Definition: Asynchronous processing allows tasks to be executed out of sequence, without waiting for the previous task to complete. Tasks can be initiated and left to run independently, allowing other tasks to proceed without blocking.

How it works: Asynchronous operations often involve callbacks, promises, or events. A task can be started, and while it’s still running, other tasks can be executed. When the asynchronous task is complete, its result is handled separately.

Example: A person starts brewing coffee, then while the coffee is brewing, they begin frying eggs. While the eggs are frying, they might start toasting bread. The tasks are overlapping, and the person doesn’t wait for one task to complete before starting another.

## Relationship Between the Concepts

### Concurrency and Parallelism:

Concurrency is about dealing with multiple tasks at once, which may or may not involve actual simultaneous execution (it could just be overlapping in time).
Parallelism, on the other hand, specifically involves tasks being executed at the exact same time on different processors or cores.

### Synchronous and Asynchronous:

Synchronous execution usually implies that tasks are being executed one after the other (sequentially), which can happen in both concurrent and non-concurrent contexts.
Asynchronous execution allows tasks to run independently, often leading to better performance in systems that can handle it, particularly when tasks involve waiting periods (e.g., I/O operations).

### Misconception Clarification

It's a common misconception to equate concurrency with synchronous execution and parallelism with asynchronous execution. However:

Concurrent systems can be either synchronous or asynchronous. You can have a system that handles multiple tasks (concurrently) in a blocking manner (synchronously), or you could have tasks that run independently (asynchronously) but aren't actually executed in parallel.
Parallel systems can also be synchronous or asynchronous. Tasks may be executed in parallel but still follow a synchronous order, or they can run in parallel asynchronously.

In summary:

- Concurrency is about managing multiple tasks at the same time (regardless of whether they are actually running simultaneously).

- Parallelism is about executing multiple tasks simultaneously on different processors or cores.

- Synchronous processing means tasks are done one after the other in a blocking manner.

- Asynchronous processing allows tasks to be initiated and continue independently, without blocking the progress of other tasks.

