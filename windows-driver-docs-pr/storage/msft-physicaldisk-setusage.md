---
title: SetUsage method of the MSFT\_PhysicalDisk class
description: Set or changes the intended usage for the physical disk within a concrete pool.
ms.assetid: E35C3D17-73E1-4319-A993-30BCE01B9B87
keywords:
- SetUsage method Windows Storage Management API
- SetUsage method Windows Storage Management API , MSFT_PhysicalDisk class
- MSFT_PhysicalDisk class Windows Storage Management API , SetUsage method
topic_type:
- apiref
ms.topic: reference
api_name:
- MSFT_PhysicalDisk.SetUsage
api_location:
- Root\Microsoft\Windows\Storage
api_type:
- COM
ms.author: windowssdkdev
ms.date: 05/31/2018
---

# SetUsage method of the MSFT\_PhysicalDisk class

Set or changes the intended usage for the physical disk within a concrete pool.

Storage pools are required to follow the assigned policy for a physical disk.

## Syntax


```mof
UInt32 SetUsage(
  [in]  UInt16 Usage,
  [out] String ExtendedStatus
);
```



## Parameters

 

*Usage* \[in\]
 

The intended usage for the physical disk. This parameter is required and cannot be NULL.



| Value                                                                                                                                                                                                                                               | Meaning                                                                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Data Store** 1              | This physical disk should only be used for data storage.                                                                                                                                                                                                                       |
|  **Manual-Select** 2  | This physical disk should only be used if manually selected by an administrator at the time of virtual disk creation. A manual-select disk is selected using the *PhysicalDisksToUse* parameter of the [**CreateVirtualDisk**](createvirtualdisk-msft-storagepool.md) method. |
|  **Hot Spare** 3                  | This physical disk should be used as a hot spare.                                                                                                                                                                                                                              |
|  **Retired** 4                          | This physical disk should be retired from use. At a minimum, no new allocations should go to this disk. If the virtual disks that reside on this disk are repaired, the data should be moved to another active physical disk.                                                  |
|  **Journal** 5                          | This physical disk should be used as a cache for other devices comprising a virtual disk. It will back a virtual disk s write-back cache, if configured.                                                                                                                       |



 

 

*ExtendedStatus* \[out\]
 

A string that contains an embedded [**MSFT\_StorageExtendedStatus**](msft-storageextendedstatus.md) object.

This parameter allows the storage provider to return extended (implementation-specific) error information.

 

## Return value

 

**Success** (0)
 

**Not Supported** (1)
 

**Unspecified Error** (2)
 

**Timeout** (3)
 

**Failed** (4)
 

**Invalid Parameter** (5)
 

**Access denied** (40001)
 

**There are not enough resources to complete the operation.** (40002)
 

**Cannot connect to the storage provider.** (46000)
 

**The storage provider cannot connect to the storage subsystem.** (46001)
 

**The storage pool could not complete the operation because its health or operational status does not permit it.** (48006)
 

**The storage pool could not complete the operation because its configuration is read-only.** (48007)
 

## Requirements



| Requirement | Value |
|-------------------------------------|-------------------------------------------------------------------------------------------|
| Minimum supported client | Windows 8 \[desktop apps only\]                                                |
| Minimum supported server | Windows Server 2012 \[desktop apps only\]                                      |
| Namespace                | Root\\Microsoft\\Windows\\Storage                                              |
| MOF                      |  Storagewmi.mof  |



## See also

 

[**MSFT\_PhysicalDisk**](msft-physicaldisk.md)
 

 

 





