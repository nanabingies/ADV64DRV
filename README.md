# ADV64DRV
 Reverse Engineering ADV64 Kernel Driver

 ## DESCRIPTION

File Name: ADV64DRV.sys

File Size: 13.80 KB (14128 bytes)

MD5: 778B7FEEA3C750D44745D3BF294BD4CE

SHA-1: 2261198385D62D2117F50F631652EDED0ECC71DB


[See full IDA disasembly](ida.asm)




## IMPORTS

Address &emsb; &emsb; &emsb; Name &emsb; &emsb; &emsb; Library &emsb; &emsb; &emsb;

0000000000012000		HalTranslateBusAddress	    HAL

0000000000012010		RtlAppendUnicodeToString	ntoskrnl

0000000000012018		RtlInitUnicodeString	    ntoskrnl

0000000000012020		MmUnmapIoSpace	            ntoskrnl

0000000000012028		MmMapIoSpace	            ntoskrnl

0000000000012030		IoWriteErrorLogEntry	    ntoskrnl

0000000000012038		IoDeleteSymbolicLink	    ntoskrnl

0000000000012040		IoDeleteDevice	            ntoskrnl

0000000000012048		IoCreateSymbolicLink	    ntoskrnl

0000000000012050		IoCreateDevice	            ntoskrnl

0000000000012058		KeBugCheckEx	            ntoskrnl

0000000000012060		IoAllocateErrorLogEntry	    ntoskrnl

0000000000012068		IofCompleteRequest	        ntoskrnl


## EXPORTS
Only DriverEntry


## DRIVER INITIALIZATION
The driver initialization function exists at offset *0x11500* which calls function *sub_11170* to initialize the device driver and create symbolic links. In the case of an error, the *IoWriteErrorLogEntry* routine queues the given error log packet to the system error logging thread.

### IRP DISPATCH ROUTINES

[sub_11010](sub_11010.asm) -> IRP_MJ_CREATE 

[sub_11010](sub_11010.asm) -> IRP_MJ_CLOSE

[sub_11460](sub_11460.asm) -> IRP_MJ_DEVICE_CONTROL

[sub_113D0](sub_113D0.asm) -> DRIVER_UNLOAD

![alt text](dispatch_routines.png)

The driver sets up a [driver unload function](driverunload.com) 


