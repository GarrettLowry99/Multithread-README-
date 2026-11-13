# Creating Multiple Threads


## Python 

```python
import threading


def do_work(name):
    print(f"{name} is working")


threads = [
    threading.Thread(target=do_work, args=("Task 1",)),
    threading.Thread(target=do_work, args=("Task 2",)),
]

for thread in threads:
    thread.start()

for thread in threads:
    thread.join()

print("All tasks are finished")
```

Call `start()` to begin each thread and `join()` to wait for all threads to finish. Avoid having threads change the same data at the same time unless you protect that data with synchronization.
