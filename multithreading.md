
# Python Concurrency: Easy Notes with Examples

---

## 🧠 Exploring Concurrency in Python

### What Is Concurrency?
Concurrency is when a program manages multiple tasks at once, but not necessarily executing them at the exact same time.

➡️ **Analogy:** A chef cooking multiple dishes by switching between them quickly.

### What Is Parallelism?
Parallelism is when multiple tasks *are actually executed* at the same time using multiple CPU cores.

➡️ **Analogy:** Multiple chefs each cooking a dish simultaneously.

### When Is Concurrency Useful?
- When tasks spend time waiting (e.g., reading files, fetching from the internet)
- Useful in I/O-bound programs to keep other tasks moving forward while waiting

---

## 🚀 Speeding Up an I/O-Bound Program

### Synchronous Version
```python
import requests
import time

urls = ["https://httpbin.org/delay/1"] * 5
start = time.time()

for url in urls:
    response = requests.get(url)
    print(response.status_code)

print(f"Total Time: {time.time() - start:.2f} seconds")
```
🔍 **Explanation:** This blocks each request, waiting for the response from one before moving to the next. It results in roughly 5 seconds of wait time for 5 requests.

### Multi-Threaded Version
```python
import threading
import requests
import time

def fetch(url):
    response = requests.get(url)
    print(response.status_code)

urls = ["https://httpbin.org/delay/1"] * 5
threads = []
start = time.time()

for url in urls:
    t = threading.Thread(target=fetch, args=(url,))
    threads.append(t)
    t.start()

for t in threads:
    t.join()

print(f"Total Time: {time.time() - start:.2f} seconds")
```
🔍 **Explanation:** Threads are created to run the `fetch` function concurrently. The program starts all threads at once and then waits for them to complete with `join()`. This reduces the wait time compared to the synchronous version.

### Asynchronous Version
```python
import asyncio
import aiohttp
import time

async def fetch(session, url):
    async with session.get(url) as response:
        print(response.status)

async def main():
    urls = ["https://httpbin.org/delay/1"] * 5
    async with aiohttp.ClientSession() as session:
        tasks = [fetch(session, url) for url in urls]
        await asyncio.gather(*tasks)

start = time.time()
asyncio.run(main())
print(f"Total Time: {time.time() - start:.2f} seconds")
```
🔍 **Explanation:** Async IO allows the program to send requests without blocking while waiting for responses. The requests are processed "concurrently" but without threads. This is faster for many I/O-bound tasks.

### Process-Based Version
```python
from multiprocessing import Pool
import requests
import time

def fetch(url):
    response = requests.get(url)
    return response.status_code

urls = ["https://httpbin.org/delay/1"] * 5
start = time.time()

with Pool(5) as p:
    print(p.map(fetch, urls))

print(f"Total Time: {time.time() - start:.2f} seconds")
```
🔍 **Explanation:** Here, multiple processes are spawned using `multiprocessing.Pool`, each handling a request in parallel, making this the fastest method for I/O-bound tasks if multiple CPUs are available.

---

## ⚡ Speeding Up a CPU-Bound Program

### Synchronous Version
```python
import time

def compute(n):
    return sum(i * i for i in range(n))

start = time.time()
results = [compute(10_000_000) for _ in range(5)]
print(results)
print(f"Total Time: {time.time() - start:.2f} seconds")
```
🔍 **Explanation:** The synchronous version calculates the sum of squares for a given range. It runs sequentially, resulting in a longer time for CPU-heavy tasks.

### Multi-Threaded Version (No improvement due to GIL)
```python
import threading
import time

def compute(n):
    print(sum(i * i for i in range(n)))

start = time.time()
threads = [threading.Thread(target=compute, args=(10_000_000,)) for _ in range(5)]

for t in threads: t.start()
for t in threads: t.join()

print(f"Total Time: {time.time() - start:.2f} seconds")
```
🔍 **Explanation:** Threads don’t provide an improvement here due to the Global Interpreter Lock (GIL) in Python, which restricts true parallel execution for CPU-bound tasks.

### Process-Based Version (Best choice)
```python
from multiprocessing import Pool
import time

def compute(n):
    return sum(i * i for i in range(n))

start = time.time()
with Pool(5) as p:
    results = p.map(compute, [10_000_000] * 5)
    print(results)

print(f"Total Time: {time.time() - start:.2f} seconds")
```
🔍 **Explanation:** By using `multiprocessing.Pool`, each task runs in a separate process, enabling real parallelism and making this the best method for CPU-heavy operations.

---

## 🔍 Deciding When to Use Concurrency

| Task Type     | Use This                |
|---------------|-------------------------|
| I/O-bound     | Async IO or Threads     |
| CPU-bound     | Multiprocessing         |
| Real-time UI  | Threads                 |

---

## 🧩 Understanding the GIL (Global Interpreter Lock)

### What Problem Did GIL Solve?
- Prevents multiple native threads from executing Python bytecodes at once.
- Ensures memory safety for CPython’s reference counting.

### Why Was the GIL Chosen?
- Simplified memory management
- Made single-thread performance better

### Impact on Multi-Threaded Programs
- CPU-bound threads can’t run in parallel
- I/O-bound threads are fine (because GIL is released during I/O)

### Why Hasn’t It Been Removed?
- Hard to maintain backward compatibility
- Would slow down many single-threaded programs

### Why Not Removed in Python 3?
- Developers prioritized stability and performance

### How to Deal With It?
- Use `multiprocessing` for CPU-heavy tasks
- Use `threading` or `asyncio` for I/O-bound tasks

---

## 💻 Setting Up Environment
```bash
pip install aiohttp
```
Needed for async HTTP requests.

---

## 🌐 10,000-Foot View of Async IO

### Where Does Async IO Fit In?
When you need to handle many tasks that wait for external operations like API calls, disk reads, etc.

### Async IO Explained Simply
It lets your program “do something else” while waiting for something to complete.

### async/await Syntax
```python
import asyncio

async def say_hello():
    print("Hello")
    await asyncio.sleep(1)
    print("World")

asyncio.run(say_hello())
```

---

## 🔁 Async Patterns

### Chaining Coroutines
```python
async def get_number():
    await asyncio.sleep(1)
    return 42

async def print_number():
    num = await get_number()
    print(num)

asyncio.run(print_number())
```

### Using a Queue
```python
import asyncio

async def producer(q):
    for i in range(5):
        await q.put(i)
        print(f"Produced {i}")
        await asyncio.sleep(0.5)

async def consumer(q):
    while True:
        item = await q.get()
        print(f"Consumed {item}")
        q.task_done()

async def main():
    q = asyncio.Queue()
    await asyncio.gather(producer(q), consumer(q))

# Run it for a limited time
asyncio.run(asyncio.wait_for(main(), timeout=3))
```

### Async for & Generators
```python
async def countdown():
    for i in range(3, 0, -1):
        yield i
        await asyncio.sleep(1)

async def main():
    async for number in countdown():
        print(number)

asyncio.run(main())
```

### asyncio.run()
```python
async def hello():
    print("Hello Async")

asyncio.run(hello())
```

---

## 🧵 Threading in Python

### What Is a Thread?
A small unit of execution in a process. Great for I/O-bound tasks.

### Starting a Thread
```python
import threading

def task():
    print("Running in a thread")

thread = threading.Thread(target=task)
thread.start()
thread.join()
```

### Daemon Threads
These automatically close when the main program ends.
```python
thread = threading.Thread(target=task, daemon=True)
thread.start()
```

### ThreadPoolExecutor
```python
from concurrent.futures import ThreadPoolExecutor

def fetch_data():
    return "Data received"

with ThreadPoolExecutor(max_workers=2) as executor:
    results = list(executor.map(lambda _: fetch_data(), range(4)))
    print(results)
```

### Race Conditions
Occurs when threads share data and timing issues cause errors.

### Lock
```python
import threading
lock = threading.Lock()

with lock:
    # safe access
    pass
```

### Deadlock
Two threads waiting on each other = freeze! Avoid by careful locking.

### Producer-Consumer Using Queue
```python
import threading
import queue
import time

q = queue.Queue()

def producer():
    for i in range(5):
        print(f"Produced {i}")
        q.put(i)
        time.sleep(1)

def consumer():
    while True:
        item = q.get()
        if item is None:
            break
        print(f"Consumed {item}")
        q.task_done()

threading.Thread(target=producer).start()
threading.Thread(target=consumer).start()
```

---

## 🎓 Flashcards for Interview Prep

**Q: What is the difference between concurrency and parallelism?**  
A: Concurrency is managing multiple tasks at once, while parallelism is executing multiple tasks at the same time using multiple CPUs.

**Q: How do you deal with Python's GIL in CPU-bound tasks?**  
A: Use multiprocessing, as it bypasses the GIL by running tasks in separate processes.

**Q: When is async IO beneficial?**  
A: It is ideal for I/O-bound tasks, like fetching data from APIs, where the program can continue doing other work while waiting for I/O operations.

---
