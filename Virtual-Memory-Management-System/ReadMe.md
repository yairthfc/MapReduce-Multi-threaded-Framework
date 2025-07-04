

# Hierarchical Virtual Memory Management System

This project implements a **virtual memory management system in C++** using hierarchical page tables. It was developed as part of an Operating Systems course at HUJI and simulates low-level memory operations including translation, allocation, swapping, and eviction — all under strict memory usage constraints.

---

## 🧠 Core Concepts

- **Hierarchical Page Tables**  
  Used to translate virtual addresses into physical addresses using multi-level table traversal.

- **Page Fault Handling**  
  On-demand page loading and frame allocation triggered by memory faults.

- **No Dynamic Memory Allocation**  
  The system is implemented using only statically defined physical memory; no `malloc` or `new`.

- **Custom Page Replacement Algorithm**  
  Eviction is based on a **cyclical distance metric**, minimizing impact on frequently accessed pages.

---

## 🚀 Features

- **Virtual to Physical Address Translation**  
  Traverses multiple levels of page tables to resolve virtual addresses.

- **Page Swapping and Eviction**  
  Swaps pages in/out of simulated memory when no free frames remain.

- **Efficient Memory Search with DFS**  
  Searches available frames using Depth-First Search for optimal placement or replacement.

- **Zero Heap Usage**  
  Implementation strictly adheres to static memory models, mimicking constrained OS environments.

- **Test Coverage**  
  Includes external test case to validate correctness of translation and replacement.

---

## ⚙️ How It Works

1. **Memory Initialization**  
   The root of the page table hierarchy is stored in frame 0.

2. **Address Translation**  
   Virtual addresses are broken into segments and translated through hierarchical page tables.

3. **Page Fault Handling**  
   When a page is not present, the system allocates a new frame or evicts one if memory is full.

4. **Page Replacement Algorithm**  
   Uses a cyclical distance metric (based on least-recently-used approximation) to choose a frame to evict.

---

## 📁 Project Structure

| File | Description |
|------|-------------|
| `VirtualMemory.h` | Public API for managing virtual memory |
| `VirtualMemory.cpp` | Core logic: translation, faults, page table traversal |
| `PhysicalMemory.h` | Interface for simulated physical memory |
| `PhysicalMemory.cpp` | Page-level memory simulation: read/write access |
| `MemoryConstants.h` | Constants: frame size, memory size, address space |
| `SimpleTest.cpp` | External test case (not written by me) to validate functionality |

---

## 🧪 Tests

The repository includes a test case: `SimpleTest.cpp`

### To enable and run the test:

1. Open `CMakeLists.txt`
2. Uncomment the line for `SimpleTest.cpp`
3. Build and run:
   ```bash
   cmake .
   make
   ./test_executable_name
   ```

> Note: The test was provided externally and used for evaluation only.

---

## 📦 Compilation

To build the project:
```bash
make
```

To clean:
```bash
make clean
```

Ensure your environment has a compatible `g++` compiler and `cmake` if you use the test system.

---

## 📜 License

This project was developed as part of the Operating Systems course at the Hebrew University of Jerusalem and is intended for academic and educational use only.

---

## 📬 Contact

For questions or collaboration:
- 📧 Email: yairthfc@gmail.com
- 🔗 LinkedIn: [linkedin.com/in/yairmahfud](https://www.linkedin.com/in/yairmahfud)
