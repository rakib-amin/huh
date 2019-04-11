- *How does a debugger work?* [Credit: ya23 & Rob Walker](https://stackoverflow.com/questions/216819/how-does-a-debugger-work)



The details of how a debugger works will depend on what you are debugging, and what the OS is. For native debugging on Windows you can find some details on MSDN: Win32 Debugging API.

The user tells the debugger which process to attach to, either by name or by process ID. If it is a name then the debugger will look up the process ID, and initiate the debug session via a system call; under Windows this would be DebugActiveProcess.

Once attached, the debugger will enter an event loop much like for any UI, but instead of events coming from the windowing system, the OS will generate events based on what happens in the process being debugged – for example an exception occurring. See WaitForDebugEvent.

The debugger is able to read and write the target process' virtual memory, and even adjust its register values through APIs provided by the OS. See the list of debugging functions for Windows.

The debugger is able to use information from symbol files to translate from addresses to variable names and locations in the source code. The symbol file information is a separate set of APIs and isn't a core part of the OS as such. On Windows this is through the Debug Interface Access SDK.

If you are debugging a managed environment (.NET, Java, etc.) the process will typically look similar, but the details are different, as the virtual machine environment provides the debug API rather than the underlying OS.


