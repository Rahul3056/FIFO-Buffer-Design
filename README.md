###  FIFO Buffer Design

#### **Concept Overview**  
A **FIFO (First-In First-Out) buffer** is a memory structure that stores data in the order it arrives. The first data entered is the first to be removed, like a queue. FIFOs are widely used in **data streaming**, **synchronization between different clock domains**, and **communication protocols**.

#### **Detailed Explanation**  
- **Inputs:**  
  - `clk`: Clock signal  
  - `rst`: Reset  
  - `wr_en`: Write enable  
  - `rd_en`: Read enable  
  - `din`: Data input  

- **Outputs:**  
  - `dout`: Data output  
  - `full`: Indicates FIFO is full  
  - `empty`: Indicates FIFO is empty  

- **Pointers:**  
  - `write_ptr` and `read_ptr` track locations for writing and reading  
  - Wrap around when the end of memory is reached  

- **Status Flags:**  
  - `full` is asserted when write pointer is one ahead of read pointer  
  - `empty` is asserted when both pointers are equal  

#### **Applications**  
- UARTs and network routers  
- Video streaming buffers  
- Pipeline stages for data integrity across modules  

#### **Execution Steps**  
1. Declare memory array, write/read pointers, and status flags.  
2. On `wr_en`, store `din` at write pointer and increment it.  
3. On `rd_en`, output `dout` from read pointer and increment it.  
4. Update `full` and `empty` flags accordingly.  
5. Write testbench to simulate push and pop operations.

#### **Real-World Example for Practice**  
Design a 16-depth FIFO buffer that handles 8-bit parallel input and output, and simulate burst reads and writes.

#### **Further Enhancements**  
- Implement synchronous FIFO with gray-coded pointers  
- Use dual-clock FIFO for interfacing different clock domains  
- Add error checking on overflow and underflow  
