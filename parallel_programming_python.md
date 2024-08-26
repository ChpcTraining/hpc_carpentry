# Table of Contents

- [Theory](#theory)
  - [Concurrency vs. Parallelism](#concurrency-vs-parallelism)
    - [Concurrency](#concurrency)
    - [Parallelism](#parallelism)
  - [Synchronous vs. Asynchronous](#synchronous-vs-asynchronous)
    - [Synchronous](#synchronous)
    - [Asynchronous](#asynchronous)
  - [Relationship Between the Concepts](#relationship-between-the-concepts)
    - [Concurrency and Parallelism](#concurrency-and-parallelism)
    - [Synchronous and Asynchronous](#synchronous-and-asynchronous)
    - [Misconception Clarification](#misconception-clarification)
- [Application](#application)
  - [1. Concurrent vs. Parallel](#1-concurrent-vs-parallel)
  - [2. Synchronous vs. Asynchronous](#2-synchronous-vs-asynchronous)
- [Guides](#guides)

# Theory

## Concurrency vs. Parallelism

### Concurrency:

Definition: Concurrency refers to the ability of a system to handle multiple tasks or processes simultaneously in an overlapping manner. However, these tasks might not be executing at the exact same time.

How it works: In a concurrent system, multiple tasks are in progress at the same time, but they may be interleaved on a single core or processor. For example, while one task is waiting for input/output (I/O), another task might be executed. This gives the illusion of parallelism.

Example: Imagine a single chef preparing multiple dishes. The chef might start chopping vegetables for one dish, then while they are simmering, they start cooking another dish. The chef switches between tasks, but only one task is actively being executed at any moment.

![image](https://github.com/user-attachments/assets/bab56c0b-3585-4217-bca4-d101506ee909)


### Parallelism:

Definition: Parallelism is a type of concurrency where multiple tasks are executed simultaneously across multiple cores or processors. Parallelism involves actually running multiple tasks at the same time.

How it works: Parallelism requires multiple processors or cores. Different tasks or parts of a task are assigned to different processors, allowing them to be executed simultaneously.

Example: Imagine having multiple chefs in a kitchen, each preparing a different dish at the same time. Here, multiple tasks (dishes) are truly being executed in parallel.

![image](https://github.com/user-attachments/assets/e82845c4-600c-4750-97da-58c0b91c1209)

![image](https://github.com/user-attachments/assets/31a05fff-b9cf-426a-a7f7-88acabf0c177)


## Synchronous vs. Asynchronous

### Synchronous:

Definition: In a synchronous process, tasks are executed sequentially, meaning each task must complete before the next one can begin, concept of blocking. The tasks are typically executed in a blocking manner, where one task waits for the previous one to finish.

How it works: Synchronous operations are straightforward—each step waits for the previous step to complete. This is often easier to reason about but can be inefficient if a task is idle or waiting for something (like I/O).

Example: A person making breakfast might toast bread, then fry eggs, and finally brew coffee. They wait for the toast to finish before starting the eggs, and then for the eggs to finish before starting the coffee.

![image](https://github.com/user-attachments/assets/4ad5e390-6f4b-426b-ace2-7fc5adf027ac)




### Asynchronous:

Definition: Asynchronous processing allows tasks to be executed out of sequence, without waiting for the previous task to complete. Tasks can be initiated and left to run independently, allowing other tasks to proceed without blocking.

How it works: Asynchronous operations often involve callbacks, promises, or events. A task can be started, and while it’s still running, other tasks can be executed. When the asynchronous task is complete, its result is handled separately.

Example: A person starts brewing coffee, then while the coffee is brewing, they begin frying eggs. While the eggs are frying, they might start toasting bread. The tasks are overlapping, and the person doesn’t wait for one task to complete before starting another.

![image](https://github.com/user-attachments/assets/acee7edc-8bf4-4b41-a204-aa661517ee6a)

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

# Application

## 1. Concurrent vs. Parallel:

Concurrent: All three applications (Chrome, Word, and Outlook) are running concurrently on your laptop. Your operating system is managing these processes in a way that allows them to run simultaneously. They can be in different states (e.g., one is actively running, another is waiting for input, etc.), and they can share resources like CPU, memory, and I/O.

Parallel: Since your laptop has 8 cores, some of these processes might be running in parallel. For instance, Chrome might be using one core, Word might be using another, and Outlook might be using a third core. This is true parallelism—each application is being processed simultaneously on different CPU cores.

## 2. Synchronous vs. Asynchronous:

Synchronous: If a process within any of these applications is blocking—meaning it must wait for one task to finish before starting another—then it's operating synchronously. For example, if you open a file in Word and it waits for the file to be fully loaded before you can start typing, that part of the process is synchronous.

Asynchronous: Modern applications often perform many tasks asynchronously to improve responsiveness. For example:
When you open Chrome and start typing a URL, Chrome may simultaneously be loading tabs from a previous session in the background (asynchronously).
Outlook might be synchronizing your email in the background while you read an email (asynchronously).
Word might auto-save your document while you continue typing, without blocking you from editing (asynchronously).

In Summary:

Concurrent: Yes, the processes (Chrome, Word, and Outlook) are concurrent because they are running at the same time, sharing system resources.

Parallel: Yes, since your laptop has multiple cores, these processes can also be running in parallel, each on a different core.

Synchronous: Some parts of these applications may perform tasks synchronously, where one task must complete before another starts (e.g., loading a 
document).

Asynchronous: Many tasks within these applications are likely asynchronous, where multiple tasks (like loading, saving, and synchronizing) happen simultaneously without waiting for each other to complete.
So, when you open Google Chrome, Microsoft Word, and Outlook on your laptop:

- They are concurrent because they are all active at the same time.
- They might be running in parallel across different CPU cores.
- Some operations within each app might be synchronous (one task after another).
- Many operations, especially background tasks, are likely asynchronous (happening independently and concurrently).

# Guides

https://www.hpc-carpentry.org/hpc-python/

https://carpentries-incubator.github.io/lesson-parallel-python/01-introduction/index.html

https://docs.dask.org/en/stable/dataframe.html

https://www.slingacademy.com/article/how-to-handle-large-datasets-with-pandas-and-dask-4-examples/#google_vignette

https://carpentries-incubator.github.io/lesson-gpu-programming/cupy.html

# Images

![image](https://github.com/user-attachments/assets/0faaa6fd-d649-4d65-b23e-a780440cce78)

![image](https://github.com/user-attachments/assets/901dac73-2a62-4ccb-bb7d-f2d6c06aa1c0)

![image](https://github.com/user-attachments/assets/e722d6cb-2957-4a9f-af65-2760271fd797)



