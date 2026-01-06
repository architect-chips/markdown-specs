

# Runtime environment

![Diagram illustrating the Runtime environment. The diagram shows two main components: a Compilation tool and the Runtime environment. The Compilation tool contains Caffe model, Caffe params, NVDC (Caffe Parser, Compiler), and Loadable. The Loadable is loaded into the Runtime environment. The Runtime environment consists of User Application Software, UMD (Runtime), KMD, and DLA HW, connected by layers (Portability layer).](21ac95be2778732e577d82233d5ee6ab_img.jpg)

Diagram illustrating the Runtime environment. The diagram shows two main components: a Compilation tool and the Runtime environment. The Compilation tool contains Caffe model, Caffe params, NVDC (Caffe Parser, Compiler), and Loadable. The Loadable is loaded into the Runtime environment. The Runtime environment consists of User Application Software, UMD (Runtime), KMD, and DLA HW, connected by layers (Portability layer).

The runtime environment includes software to run a compiled neural network on compatible NVDLA (./glossary.html#term-NVDLA) hardware. It consists of 2 parts:

- User Mode Driver - This is the main interface to the application. As detailed in the Compiler library (compilation\_tool.html#compiler-library), after parsing and compiling the neural network layer by layer, the compiled output is stored in a file format called NVDLA Loadable (./glossary.html#term-NVDLA-Loadable). User mode runtime driver loads this loadable and submits inference jobs to the Kernel Mode Driver.
- Kernel Mode Driver - Consists of kernel mode driver and engine scheduler that does the work of scheduling the compiled network on NVDLA (./glossary.html#term-NVDLA) and programming the NVDLA (./glossary.html#term-NVDLA) registers to configure each functional block.

The runtime environment uses the stored representation of the network saved as NVDLA Loadable (./glossary.html#term-NVDLA-Loadable) image. From point of view of the NVDLA Loadable (./glossary.html#term-NVDLA-Loadable), each compiled "layer" in software is loadable on a functional block in the NVDLA (./glossary.html#term-NVDLA) implementation. Each layer includes information about its dependencies on other layers, the buffers that it uses for inputs and outputs in memory, and the specific configuration of each functional block used for its execution. Layers are linked together through a dependency graph, which the engine scheduler uses for scheduling layers. The format of an NVDLA Loadable (./glossary.html#term-NVDLA-Loadable) is standardized across compiler implementations and UMD implementations. All implementations that comply with the NVDLA (./glossary.html#term-NVDLA) standard should be able to at least interpret any NVDLA Loadable (./glossary.html#term-NVDLA-Loadable) image, even if the implementation may not have some features that are required to run inferencing using that loadable image.

Both the User Mode Driver stack and the Kernel Mode Driver stack exist as defined APIs, and are expected to be wrapped with a system portability layer. Maintaining core implementations within a portability layer is expected to require relatively few changes. This expedites any effort that may be necessary to run the NVDLA (./glossary.html#term-NVDLA) software-stack on multiple platforms. With the appropriate portability layers in place, the same core implementations should compile as readily on both Linux and FreeRTOS. Similarly, on “headed” implementations that have a microcontroller closely coupled to NVDLA (./glossary.html#term-NVDLA), the existence of the portability layer makes it possible to run the same kernel mode driver on that microcontroller as would have run on the main CPU in a “headless” implementation that had no such companion microcontroller.

## User Mode Driver

![Diagram illustrating the User Mode Driver (UMD) stack structure within the Runtime environment. The stack consists of User Application Software, UMD, Portability layer, KMD, and DLA HW. The UMD is loaded by a Loadable component. The UMD and KMD are connected via a bidirectional arrow, passing through the Portability layer. The KMD is connected to DLA HW via a bidirectional arrow, also passing through the Portability layer. The entire stack is enclosed in a dashed box labeled 'Runtime environment'.](8d2f4e036a5e0205a1ea3f0b3378f584_img.jpg)

Diagram illustrating the User Mode Driver (UMD) stack structure within the Runtime environment. The stack consists of User Application Software, UMD, Portability layer, KMD, and DLA HW. The UMD is loaded by a Loadable component. The UMD and KMD are connected via a bidirectional arrow, passing through the Portability layer. The KMD is connected to DLA HW via a bidirectional arrow, also passing through the Portability layer. The entire stack is enclosed in a dashed box labeled 'Runtime environment'.

UMD provides standard Application Programming Interface (API) for processing loadable images, binding input and output tensors to memory locations, and submitting inference jobs to KMD. This layer loads the network into memory in a defined set of data structures, and passes it to the KMD in an implementation-defined fashion. On Linux, for instance, this could be an `ioctl()`, passing data from the user-mode driver to the kernel-mode driver; on a single-process system in which the KMD runs in the same environment as the UMD, this could be a simple function call. Low-level functions are implemented in User Mode Driver

## Application Programming Interface

## Runtime Interface

This is the interface for runtime library. It implements functions to process loadable buffer passed from application after reading it from file, allocate memory for tensors and intermediate buffers, prepare synchronization points and finally submit inference job to KMD. Inference job submitted to KMD is referred as DLA task.

### **class nvdla :: IRuntime**

Submitting task for inference using runtime interface includes below steps

1. Create NVDLA runtime instance
2. Get NVDLA device information
3. Load network data
4. Get input and output tensors information
5. Update input and output tensors information
6. Allocate memory for input and output tensors
7. Bind memory handle with tensor
8. Submit task for inference
9. Unload network resources

#### Create NVDLA runtime instance

#### **IRuntime \* nvdla :: createRuntime ()**

**returns:** IRuntime object

#### Get NVDLA device information

#### **NvU16 nvdla :: IRuntime :: getMaxDevices ()**

Get maximum number of device supported by HW configuration. Runtime driver supports submitting inference jobs to multiple DLA devices. User application can select device to use. One task can't be split across devices but one task can be submitted to only one device.

**Returns:** Maximum number of devices supported

#### **NvU16 nvdla :: IRuntime :: getNumDevices ()**

Get number of available devices from the maximum number of devices supported by HW configuration.

**Returns:** Number of available devices

### Load network data

#### **NvError nvdlA::IRuntime :: load (const NvU8 \*buf, int instance)**

Parse loadable from buffer and update ILoadable with information required to create task

**Parameters:**

- **buf** – Loadable image buffer
- **instance** – Device instance to load this network

**Returns:** NvError

#### Get input and output tensors information

#### **NvError nvdlA::IRuntime :: getNumInputTensors (int \*input\_tensors)**

Get number of network's input tensors from loadable

**Parameters:** **input\_tensors** – Pointer to update number of input tensors value

**Returns:** NvError

#### **NvError nvdlA::IRuntime :: getInputTensorDesc (int id, NvDlaTensor \*tensors)**

Get network's input tensor descriptor

**Parameters:**

- **id** – Tensor ID
- **tensors** – Tensor descriptor

**Returns:** NvError

#### **NvError nvdlA::IRuntime :: getNumOutputTensors (int \*output\_tensors)**

Get number of network's output tensors from loadable

**Parameters:** **output\_tensors** – Pointer to update number of output tensors value

**Returns:** NvError

#### **NvError nvdlA::IRuntime :: getOutputTensorDesc (int id, NvDlaTensor \*tensors)**

Get network's output tensor descriptor

**Parameters:**

- **id** – Tensor ID
- **tensors** – Tensor descriptor

**Returns:** NvError

#### Update input and output tensors information

##### **Note**

Required only if tensor information is changed, not all parameters can be changed

#### **NvError nvdlA::IRuntime :: setInputTensorDesc (int id, const NvDlaTensor \*tensors)**

Set network's input tensor descriptor

**Parameters:** • **id** – Tensor ID  
• **tensors** – Tensor descriptor

**Returns:** NvError

**NvError** nvdl::IRuntime:: **setOutputTensorDesc** (*int id, const NvDlaTensor \*tensors*)

Set network's output tensor descriptor

**Parameters:** • **id** – Tensor ID  
• **tensors** – Tensor descriptor

**Returns:** NvError

Allocate memory for input and output tensors

**NvDlaError** **allocateSystemMemory** (*void \*\*h\_mem, NvU64 size, void \*\*pData*)

Allocate DMA memory accessible by NVDLA for input and output tensors.

**Parameters:** • **h\_mem** – void pointer to store memory handle address  
• **size** – Size of memory to allocate  
• **pData** – Virtual address for allocated memory

**Returns:** NvError

Bind memory handle with tensor

**NvError** nvdl::IRuntime:: **bindInputTensor** (*int id, void \*hMem*)

Bind network's input tensor to memory handle

**Parameters:** • **id** – Tensor ID  
• **hMem** – DLA memory handle returned by **allocateSystemMemory**()

**Returns:** NvError

**NvError** nvdl::IRuntime:: **bindOutputTensor** (*int id, void \*hMem*)

Bind network's output tensor to memory handle

**Parameters:** • **id** – Tensor ID  
• **hMem** – DLA memory handle returned by **allocateSystemMemory**()

**Returns:** NvError

Submit task for inference

**NvError** nvdl::IRuntime:: **submit** ()

Submit task for inference, it is blocking call

**Returns:** NvError

Unload network resources

**NvError** nvdlai::IRuntime:: **unLoad (int instance)**

Unload network data, free all resourced used for network if no plan to submit inference using same network

**Parameters:** **instance** – Device instance from where to unload**Returns:** NvError

### Portability layer

Portability layer for UMD implements functions to access NVDLA device, allocate DMA memory and submit task to low level driver. For this functionality UMD has to communicate with KMD and the communication interface is OS dependent. Portability layer abstracts this OS dependent interface.

### **type NvError**

Enum for error codes

### **type NvDLAHeap**

Memory heap to allocate memory, NVDLA supports two memory interfaces. Generally these interfaces are connected to DRAM (System memory) and internal SRAM. KMD can maintain separate heaps for allocation depending on memory type.

### **type NvDLAMemDesc**

Memory descriptor, it includes memory handle and buffer size.

### **type NvDLATask**

DLA task structure. Runtime driver populates it using information from loadable and is used by portability layer to submit inference task to KMD in an implementation define manner.

#### **NvError NvDLAInitialize (void \*\*session\_handle)**

This API should initialize session for portability layer which may include allocating some structure required to maintain information such such device context, file descriptors. This function can be empty.

**Parameters:** • **session\_handle** – [out] Pointer to update session handle address. This address is passed in any APIs called after this which can be used by portability layer to recover session information.

**Returns:** NvError

#### void NvDlaDestroy (void \*session\_handle)

Release all session resources

**Parameters:** • **session\_handle** – Session handle address obtained from `NvDlaInitialize()`

#### NvError NvDlaOpen (void \*session\_handle, NvU32 instance, void \*\*device\_handle)

This API should open DLA device instance. .

**Parameters:** • **session\_handle** – Session handle address obtained from `NvDlaInitialize()`  
• **instance** – NVDLA instance to use if there are more than one instances in SoC  
• **device\_handle** – [out] Pointer to update device context. It is used to obtain device information required for further callbacks which need device context.

**Returns:** NvError

#### void NvDlaClose (void \*session\_handle, void \*device\_handle)

Close DLA device instance

**Parameters:** • **session\_handle** – Session handle address obtained from `NvDlaInitialize()`  
• **device\_handle** – Device handle address obtained from `NvDlaOpen()`

#### NvError NvDlaSubmit (void \*session\_handle, void \*device\_handle, NvDlaTask \*tasks, NvU32 num\_tasks)

Submit inference task to KMD

**Parameters:** • **session\_handle** – Session handle address obtained from `NvDlaInitialize()`  
• **device\_handle** – Device handle address obtained from `NvDlaOpen()`  
• **tasks** – Lists of tasks to submit for inferencing  
• **num\_tasks** – Number of tasks to submit

**Returns:** NvError

#### NvError NvDlaAllocMem (void \*session\_handle, void \*device\_handle, void \*\*mem\_handle, void \*\*pData, NvU32 size, NvDlaHeap heap)

Allocate, pin and map DLA engine accessible memory. For example, in case of systems where DLA is behind IOMMU then this call should ensure that IOMMU mappings are created for this memory. In case of Linux, internal implementation can use readily available frameworks such as ION for this.

**Parameters:** • **session\_handle** – Session handle address obtained from `NvDlaInitialize()`  
• **device\_handle** – Device handle address obtained from `NvDlaOpen()`  
• **mem\_handle** – [out] Memory handle updated by this function  
• **pData** – [out] If the allocation and mapping is successful, provides a virtual address through which the memory buffer can be accessed.  
• **size** – Size of buffer to allocate  
• **heap** – Implementation defined memory heap selection

**Returns:** NvError

**NvError NvDLaFreeMem (void \*session\_handle, void \*device\_handle, void \*mem\_handle, void \*pData, NvU32 size)**

Free DMA memory allocated using NvDLAAllocMem()

**Parameters:**

- **session\_handle** – Session handle address obtained from NvDLaInitialize()
- **device\_handle** – Device handle address obtained from NvDLaOpen()
- **mem\_handle** – Memory handle address obtained from NvDLAAllocMem()
- **pData** – Virtual address returned by NvDLAAllocMem()
- **size** – Size of the buffer allocated

**Returns:** NvError

**void NvDLaDebugPrintf (const char \*format, ...)**

Outputs a message to the debugging console, if present.

**Parameters:** • **format** – A pointer to the format string

## Kernel Mode Driver

![Diagram illustrating the Kernel Mode Driver (KMD) architecture. The diagram shows a 'Loadable' component loading into the 'Runtime environment'. Inside the Runtime environment, 'User Application Software' interacts with 'UMD' (User Mode Driver) via a 'Portability layer'. The 'UMD' interacts with the 'KMD' (Kernel Mode Driver) via a 'Portability layer'. The 'KMD' interacts with 'DLA HW' (DLA Hardware). The image file path is (.../_images/kmd.png).](2396add2849eccefcbcfbe1c7142a253_img.jpg)

Diagram illustrating the Kernel Mode Driver (KMD) architecture. The diagram shows a 'Loadable' component loading into the 'Runtime environment'. Inside the Runtime environment, 'User Application Software' interacts with 'UMD' (User Mode Driver) via a 'Portability layer'. The 'UMD' interacts with the 'KMD' (Kernel Mode Driver) via a 'Portability layer'. The 'KMD' interacts with 'DLA HW' (DLA Hardware). The image file path is (.../\_images/kmd.png).

The KMD main entry point receives an inference job in memory, selects from multiple available jobs for execution (if on a multi-process system), and submits it to the core engine scheduler. This core engine scheduler is responsible for handling interrupts from NVDLA (.../glossary.html#term-NVDLA), scheduling layers on each individual functional block, and updating any dependencies based upon the completion of the layer. The scheduler uses information from the dependency graph to determine when subsequent layers are ready to be scheduled; this allows the compiler to decide scheduling of layers in an optimized way, and avoids performance differences from different implementations of the KMD.

![](91be14371a97fb5ce9eeb29ae18d07c3_img.jpg)

Flowchart illustrating the Core Engine Interface execution flow, showing interactions between the UMD (User Mode Driver), HW Layer, and Portability Layer.

The flow starts with `Task complete` leading to `Execute_task`. `Execute_task` leads to the decision point `HW layer pending?`.

If `HW layer pending?` is No, the flow proceeds to `Task complete`. If Yes, the flow proceeds to `HW layer done`.

`HW layer done` leads to `process_events`.

`process_events` receives input from `events` (source: `../_images/kmd_interface.png`) and `dia_isr_handler`.

`process_events` leads to `wait_for_event`.

`wait_for_event` leads to `program`.

`program` receives input from `reg_read/reg_write` and `Other functions`.

`program` leads to `wait_for_event` and `process_events`.

`reg_read/reg_write` leads to `Other functions`.

`Other functions` leads to `program`.

`wait_for_event` leads to `Interrupt`.

`Interrupt` leads to `dia_isr_handler` and `process_events`.

`Interrupt` is associated with the `Portability layer`.

## Core Engine Interface

Neural networks are converted to hardware layers for execution on DLA hardware. These layers are connected to each other using dependency graph and executed on DLA by module known as engine scheduler. This scheduler is responsible for updating dependency counts, handling events and programming hardware layers. It is the core module of DLA software and portable across different OS. Portability layer should use below interfaces to enable core engine module. Core engine module is also referenced as firmware as same source code would be used in firmware of companion controller for headed configs.

General sequence of execution in KMD is as below

1. Register driver with firmware during probe
2. Driver submits task information for execution
3. Firmware programs hardware layer
4. Interrupt received from hardware
5. Bottom half caller to process events after interrupt
6. Clean task and engine state

Register driver with firmware during probe

```
int32_t dla_register_driver (void **engine_context, void *driver_context)
```

This function must be called once during boot to initialize DLA engine scheduler and register driver with firmware before submitting any task. Pass pointer to driver context in @param driver\_context which is passed as param when firmware calls any function of portability layer. It also updates pointer to engine context which must be passed in any function call to firmware after this point.

**Parameters:**

- **engine\_context** – Pointer to engine specific data
- **driver\_context** – Pointer to driver specific data

**Returns:** 0 on success and negative on error

Driver submits task information for execution

#### type dla\_task\_descriptor

Task descriptor structure. This structure includes all the information required to execute a network such as number of layers, dependency graph address etc.

#### int32\_t dla\_execute\_task (void \*engine\_context, void \*task\_data)

This function initializes sub-engines and starts task execution. Further programming and layer scheduling is triggered by events received from hardware.

**Parameters:**

- **engine\_context** – Engine specific data received in `dla_register_driver()`
- **task\_data** – Task specific data to be passed when reading task info

**Returns:** 0 on success and negative on error

Interrupt received from hardware

#### int32\_t dla\_isr\_handler (void \*engine\_context)

This function is called when DLA interrupt is received. Portability layer should register it's own handler using the mechanism supported by that platform and call this function from the handler. Call to this function must be protected by lock to prevent handling interrupt when firmware is programming layers in process context.

**Parameters:**

- **engine\_context** – Engine specific data received in `dla_register_driver()`

**Returns:** 0 on success and negative on error

Bottom half caller to process events after interrupt

#### int32\_t dla\_process\_events (void \*engine\_context, uint32\_t \*task\_complete)

Interrupt handler just records events and does not process those events. Portability layer must call this function in thread/process context after interrupt handler is done.

**Parameters:**

- **engine\_context** – Engine specific data received in `dla_register_driver()`
- **task\_complete** – Pointer to parameter to indicate task complete, firmware writes 1 to it if all layers are processed.

**Returns:** 0 on success and negative on error

Clean task and engine state

#### void dla\_clear\_task (void \*engine\_context)

This function resets engine scheduler state including op descriptor cache, error values, sub-engine status, events etc and clears previous task state from firmware. This function can be called by portability layer after task completion. It is not mandatory to call it but calling it will ensure clean state before next task execution.

**Parameters:** • **engine\_context** – Engine specific data received in `dlr_register_driver()`

**Returns:** 0 on success and negative on error

### Portability layer

Core engine module (firmware) is OS independent but it still needs some OS services such as memory allocation, read/write IO registers, interrupt notifications. Portability layer implemented in KMD should provide implementation for below interfaces to core engine module.

### Firmware programs hardware layer

#### **uint32\_t dlr\_reg\_read (void \*driver\_context, uint32\_t addr)**

Read DLA HW register. Portability layer is responsible to use correct base address and for any IO mapping if required.

**Parameters:** • **driver\_context** – Driver specific data received in `dlr_register_driver()`

• **addr** – Register offset

**Returns:** Register value

#### **void dlr\_reg\_write (void \*driver\_context, uint32\_t addr, uint32\_t reg)**

Write DLA HW register. Portability layer is responsible to use correct base address and for any IO mapping if required.

**Parameters:** • **driver\_context** – Driver specific data received in `dlr_register_driver()`

• **addr** – Register offset

• **reg** – Value to write

#### **int32\_t dlr\_read\_dma\_address (struct dlr\_task\_desc \*task\_desc, int16\_t index, void \*dst)**

Read DMA address from address list at index specified. This function is used by functional block programming operations to read address for DMA engines in functional blocks.

**Parameters:** • **task\_desc** – Task descriptor for in execution task

• **index** – Index in address list

• **dst** – Destination pointer to update address

**Returns:** 0 in case success, error code in case of failure

#### **int32\_t dlr\_read\_cpu\_address (struct dlr\_task\_desc \*task\_desc, int16\_t index, void \*dst)**

Read CPU accessible address from address list at index specified. This function is used by engine scheduler to read data from memory buffer. Address returned by this function must be accessible by processor running engine scheduler.

**Parameters:**

- **task\_desc** – Task descriptor for in execution task
- **index** – Index in address list
- **dst** – Destination pointer to update address

**Returns:** 0 in case success, error code in case of failure

**int32\_t dla\_data\_read (void \*driver\_context, void \*task\_data, uint64\_t src, void \*dst, uint32\_t size, uint64\_t offset)**

This function reads data from buffers passed by UMD in local memory. Addresses for buffers passed by are shared in address list and network descriptor contains index in address list for those buffers. Firmware reads this data from buffer shared by UMD into local buffer to consume the information.

**Parameters:**

- **driver\_context** – Driver specific data received in `dlr_register_driver()`
- **task\_data** – Task specific data received in `dlr_execute_task()`
- **src** – Index in address list
- **dst** – Local memory address
- **size** – Data size
- **offset** – Offset from start of UMD buffer

**Returns:** 0 in case success, error code in case of failure

**int32\_t dlr\_data\_write (void \*driver\_context, void \*task\_data, void \*src, uint64\_t dst, uint32\_t size, uint64\_t offset)**

This function writes data from local buffer to buffer passed by UMD. Addresses for buffers passed by are shared in address list and network descriptor contains index in address list for those buffers. Firmware writes this data to buffer shared by UMD from local buffer to update the information.

**Parameters:**

- **driver\_context** – Driver specific data received in `dlr_register_driver()`
- **task\_data** – Task specific data received in `dlr_execute_task()`
- **src** – Local memory address
- **dst** – Index in address list
- **size** – Data size
- **offset** – Offset from start of UMD buffer

**Returns:** 0 in case success, error code in case of failure

### DESTINATION\_PROCESSOR

Memory will be accessed by processor running firmware.

#### DESTINATION\_DMA

Memory will be accessed by NVDLA DMA engines

**int32\_t dlr\_get\_dma\_address (void \*driver\_context, void \*task\_data, int16\_t index, void \*dst\_ptr, uint32\_t destination)**

Some buffers shared by UMD are accessed by processor responsible for programming DLA HW. It would be companion micro-controller in case of headed config while main CPU in case of headless config. Also, some buffers are accessed by DLA DMA engines inside sub-engines. This function should return proper address accessible by destination user depending on config.

**Parameters:**

- **driver\_context** – Driver specific data received in  `dla_register_driver()`
- **task\_data** – Task specific data received in  `dla_execute_task()`
- **index** – Index in address list
- **dst\_ptr** – Pointer to update address
- **destination** – Destination user for DMA address, `DESTINATION_PROCESSOR` or `DESTINATION_DMA`

#### `int64_t dla_get_time_us (void)`

Read system time in micro-seconds

**Returns:** Time value in micro-seconds

#### `void * dla_memset (void *src, int ch, uint64_t len)`

Fills the first len bytes of the memory area pointed to by src with the constant byte ch.

**Parameters:**

- **src** – Memory area address
- **ch** – Byte to fill
- **len** – Length of memory area to fill

**Returns:** Memory area address

#### `void * dla_memcpy (void *dest, const void *src, uint64_t len)`

**Parameters:**

- **dest** – Destination memory area address
- **src** – Source memory area address
- **len** – Length of memory area to copy

**Returns:** Destination memory area address

#### `void dla_debug (const char *str, ...)`

Print debug message to console

**Parameters:**

- **str** – Format string and variable arguments

#### `void dla_info (const char *str, ...)`

Print information message to console

**Parameters:**

- **str** – Format string and variable arguments

#### `void dla_warn (const char *str, ...)`

Print warning message to console

**Parameters:**

- **str** – Format string and variable arguments

**void dla\_error (const char \*str, ...)**

Print error message to console

**Parameters:** • **str** – Format string and variable arguments