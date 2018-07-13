DLL Hijack example
==================

This project shows how it's possible to hijacking an .NET Framework application, and the current permissions, just by copying a simple DLL into the directory of the executable.

The vulnability works this way:
If someone copies a native DLL named “version.dll” in the same directory as a .NET executable, this “version.dll” is loaded and initialized (DllMain is called)., BEFORE the .NET application runs. The “version.dll” needs to have the same architecture as the .NET executable (e.g. x64).

This would be relevant for uses who download an application from somewhere, which is downloaded into the browsers download order, and started from there. Although it's adviced no to do so, what users actually follow such an advice? Most installers protect themselfs against such an attack, but to my knowledge there is not a solution for .NET applications.

I reported this to Microsoft, the answer was not very satisfactory:

_If I am interpreting your findings correctly, this report is predicated on the attacker having written a malicious binary to the directory where the application is launched from - in this case, the downloads folder. As described in the Windows library search order process, loading binaries from the application directory is by design. As your report as written, this does not meet the bar for security servicing. As such, this thread is being closed and no longer monitored._

Although I understand the reasoning, I would like to have a way to protect my .NET application against surch attacks. I hope someone might pick this up, to help and find a solution.
