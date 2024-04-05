# Creating The Driver

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

Following these, it’s time to declare the entrypoint for our driver, which we’ll call “DriverEntry”. 

```c
NTSTATUS DriverEntry(
	_In_ PDRIVER_OBJECT DriverObject,
	_In_ PUNICODE_STRING RegistryPath
)
```

**NTSTATUS** as a return type is crucial because it indicates success or failure, & usually useful debugging information such as diagnostic codes.

Both **DriverObject** and **RegistryPath** are needed parameters for the DriverEntry entrypoint function as seen on Microsoft’s official documentation. 
    __DriverObject__ is a ptr to a structure that represents the Windows Driver Model driver object.
    **RegistryPath** here is a ptr to a structure that specifies the path to the driver’s parameters in the registry.

Furthermore - as I defined this method I tried to comment as best as I could to explain what is happening. 
