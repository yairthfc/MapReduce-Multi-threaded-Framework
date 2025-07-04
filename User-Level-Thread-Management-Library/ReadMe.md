
# User-Level Thread Management Library

This project implements a **user-level thread library** for Linux-based systems. It enables efficient thread lifecycle control, scheduling, and sleep mechanisms **without relying on OS-level threading (e.g., `pthread`)**. The library is written in C++ and designed for use in systems programming and operating systems coursework.

---

## 🧠 Project Overview

This library provides **Round-Robin scheduling** with fixed time slices and **preemptive context switching** using Linux signals and timers (`setitimer`, `sigaction`). It allows thread creation, blocking, resumption, termination, and sleeping — all at the user level.

Internally, the system uses:
- A **ready queue** for scheduling
- A **sleep map** to manage suspended threads
- A **min-heap** for efficient thread ID reuse

---

## 🚀 Features

- **Thread Lifecycle Management**  
  Create, block, resume, and terminate threads entirely at the user level.

- **Preemptive Scheduling**  
  Automatic time-sliced switching via `SIGVTALRM`.

- **Sleep Functionality**  
  Threads can sleep for a specified number of quantums without blocking others.

- **Optimized Performance**  
  Fast scheduling and thread ID reuse via efficient data structures.

- **No `pthread` Dependency**  
  Fully self-contained implementation using signals and timers.

---

## 🧩 API Reference

```cpp
int uthread_init(int quantum_usecs);
// Initializes the thread library with the given quantum size in microseconds.

int uthread_spawn(thread_entry_point entry_point);
// Creates a new thread running the given function and adds it to the ready queue.

int uthread_block(int tid);
// Blocks the thread with the given ID, preventing it from running.

int uthread_resume(int tid);
// Resumes a previously blocked thread, allowing it to run again.

int uthread_sleep(int num_quantums);
// Suspends the currently running thread for the given number of quantums.

int uthread_terminate(int tid);
// Terminates the thread with the given ID.
// If tid == 0, the entire process is terminated.
```

---

## 🧪 Test Cases

The repository includes **external test cases** to verify the correctness and robustness of the thread library. These are available but commented out by default.

### To enable and run tests:
1. Open `CMakeLists.txt`
2. Uncomment the relevant test files under the `# Add tests` section
3. Build and run the tests using:
   ```bash
   cmake .
   make
   ./test_executable_name
   ```

---

## 📦 Compilation

To build the library:
```bash
make
```

To clean:
```bash
make clean
```

> Ensure you have `g++` and `make` installed.

---

## 📜 License

This project was developed as part of the Operating Systems course at the Hebrew University of Jerusalem and is intended for educational and personal use.

---

## 📬 Contact

For questions or collaboration:
- 📧 Email: yairthfc@gmail.com
- 🔗 LinkedIn: [linkedin.com/in/yairmahfud](https://www.linkedin.com/in/yairmahfud)
