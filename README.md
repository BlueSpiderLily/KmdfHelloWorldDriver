**## Creating The Driver**

For this project I prepare a small Universal Windows driver using the Kernel-Mode Driver Framework (KMDF) and then I deploy it and install it on a virtual machine inside of Window’s HyperV component.

To begin the drivers code it is important to include necessary headers/ includes. 

In this case:

    #include <ntddk.h> // “Contains core Windows kernel definitions for all drivers”
  	#include <wdf.h> // “Contains definitions for drivers based on the Windows Driver Framework (WDF)

Then I plan to use two methods, so I declare two prototypes for them before the entrypoint:

```c
//declarations for the callbacks we'll use
  DRIVER_INITIALIZE DriverEntry;
  EVT_WDF_DRIVER_DEVICE_ADD KmdfHelloWorldEvtDeviceAdd;
```
