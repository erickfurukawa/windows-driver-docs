---
title: tct (Trace to Next Call or Return)
description: The tct command executes the program until it reaches a call instruction or return instruction.
keywords: ["tct (Trace to Next Call or Return) Windows Debugging"]
ms.date: 05/23/2017
topic_type:
- apiref
ms.topic: reference
api_name:
- tct (Trace to Next Call or Return)
api_type:
- NA
---

# tct (Trace to Next Call or Return)


The **tct** command executes the program until it reaches a call instruction or return instruction.

User-Mode

```dbgcmd
[~Thread] tct [r] [= StartAddress] [Count] 
```

Kernel-Mode

```dbgcmd
tct [r] [= StartAddress] [Count] 
```

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


<span id="_______Thread______"></span><span id="_______thread______"></span><span id="_______THREAD______"></span> *Thread*   
Specifies threads to continue executing. All other threads are frozen. For more information about the syntax, see [Thread Syntax](thread-syntax.md). You can specify threads only in user mode.

<span id="_______r______"></span><span id="_______R______"></span> **r**   
Turns on and off the display of registers and flags. By default, the registers and flags are displayed. You can disable register display by using the **tctr**, [**pr**](p--step-.md), [**tr**](t--trace-.md), or .prompt\_allow -reg commands. All of these commands control the same setting and you can use any of them to override any previous use of these commands.

You can also disable register display by using the l-os command. This setting is separate from the other four commands. To control which registers and flags are displayed, use the [**rm (Register Mask)**](rm--register-mask-.md) command.

<span id="_______StartAddress______"></span><span id="_______startaddress______"></span><span id="_______STARTADDRESS______"></span> *StartAddress*   
Specifies the address where the debugger begins execution. If you do not use *StartAddress*, execution begins at the instruction that the instruction pointer points to. For more information about the syntax, see [Address and Address Range Syntax](address-and-address-range-syntax.md).

<span id="_______Count______"></span><span id="_______count______"></span><span id="_______COUNT______"></span> *Count*   
Specifies the number of **call** or **return** instructions that the debugger must encounter for the **tct** command to end. The default value is one.

### <span id="Environment"></span><span id="environment"></span><span id="ENVIRONMENT"></span>Environment

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Modes</strong></p></td>
<td align="left"><p>User mode, kernel mode</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Targets</strong></p></td>
<td align="left"><p>Live debugging only</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Platforms</strong></p></td>
<td align="left"><p>All</p></td>
</tr>
</tbody>
</table>

 

### <span id="Additional_Information"></span><span id="additional_information"></span><span id="ADDITIONAL_INFORMATION"></span>Additional Information

For more information about related commands, see [Controlling the Target](controlling-the-target.md).

## Remarks

The **tct** command causes the target to begin executing. This execution continues until the debugger reaches a **call** or **return** instruction or encounters a breakpoint.

If the program counter is already on a **call** or **return** instruction, the debugger traces into the call or return and continues executing until it encounters another **call** or **return**. This tracing, rather than execution, of the call is the only difference between **tct** and [**pct (Step to Next Call or Return)**](pct--step-to-next-call-or-return-.md).

In source mode, you can associate one source line with multiple assembly instructions. This command does not stop at a **call** or **return** instruction that is associated with the current source line.

 

 





