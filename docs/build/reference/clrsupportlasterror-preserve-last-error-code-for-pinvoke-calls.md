---
title: /CLRSUPPORTLASTERROR (Letzten Fehlercode für PInvoke-Aufrufe beibehalten)
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: 19930591c2d0406c68b1a408622a49c9e8b1d551
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322275"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (Letzten Fehlercode für PInvoke-Aufrufe beibehalten)

**/CLRSUPPORTLASTERROR**, der standardmäßig aktiviert ist, behält den letzten Fehlercode von Funktionen bei, die über den P/Invoke-Mechanismus aufgerufen werden, mit dem Sie systemeigene Funktionen in DLLS aufrufen können, aus Code, der mit **/clr**kompiliert wurde.

## <a name="syntax"></a>Syntax

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>Bemerkungen

Das Beibehalten des letzten Fehlercodes bedeutet eine Leistungsminderung.  Wenn Sie die Leistungseinbußen beim Beibehalten des letzten Fehlercodes nicht verursachen möchten, verknüpfen Sie die Verknüpfung mit **/CLRSUPPORTLASTERROR:NO**.

Sie können die Auswirkungen auf die Leistung minimieren, indem Sie mit **/CLRSUPPORTLASTERROR:SYSTEMDLL**verknüpfen, der nur den letzten Fehlercode für Funktionen in System-DLLs beibehält.  Eine System-DLL ist als eine der folgenden definiert:

|||||
|-|-|-|-|
|ACLUI. Dll|ACTIVEDS. Dll|ADPTIF. Dll|ADVAPI32. Dll|
|ASYCFILT. Dll|AUTHZ. Dll|AVICAP32. Dll|AVIFIL32. Dll|
|Kabinett. Dll|CLUSAPI. Dll|COMCTL32. Dll|COMDLG32. Dll|
|COMSVCS. Dll|CREDUI. Dll|CRYPT32. Dll|CRYPTNET. Dll|
|KRYPTUI. Dll|D3D8THK. Dll|DBGENG. Dll|DBGHELP. Dll|
|DCIMAN32. Dll|DNSAPI. Dll|DSPROP. Dll|DSUIEXT. Dll|
|GDI32. Dll|GLU32. Dll|HLINK. Dll|ICM32. Dll|
|IMAGEHLP. Dll|IMM32. Dll|IPHLPAPI. Dll|IPROP. Dll|
|Kernel32.dll. Dll|KSUSER. Dll|LOADPERF. Dll|LZ32. Dll|
|Mapi32. Dll|MGMTAPI. Dll|MOBSYNC. Dll|Mpr. Dll|
|MPRAPI. Dll|MQRT. Dll|MSACM32. Dll|MSCMS. Dll|
|Msi. Dll|MSIMG32. Dll|MSRATING. Dll|MSTASK. Dll|
|MSVFW32. Dll|MSWSOCK. Dll|MTXEX. Dll|NDDEAPI. Dll|
|NETAPI32. Dll|NPPTOOLS. Dll|NTDSAPI. Dll|NTDSBCLI. Dll|
|NTMSAPI. Dll|ODBC32. Dll|ODBCBCP. Dll|OLE32. Dll|
|OLEACC. Dll|OLEAUT32. Dll|OLEDLG. Dll|OPENGL32. Dll|
|Pdh. Dll|POWRPROF. Dll|QOSNAME. Dll|Abfrage. Dll|
|RASAPI32. Dll|RASDLG. Dll|RASSAPI. Dll|RESUTILS. Dll|
|RICHED20. Dll|RPCNS4. Dll|RPCRT4. Dll|Rtm. Dll|
|RTUTILS. Dll|SCARDDLG. Dll|SECUR32. Dll|SENSAPI. Dll|
|SETUPAPI. Dll|Sfc. Dll|SHELL32. Dll|SHFOLDER. Dll|
|SHLWAPI. Dll|SISBKUP. Dll|SNMPAPI. Dll|SRCLIENT. Dll|
|Sti. Dll|TAPI32. Dll|Verkehr. Dll|Url. Dll|
|URLMON. Dll|USER32. Dll|USERENV. Dll|USP10. Dll|
|Uxtheme. Dll|VDMDBG. Dll|Version. Dll|Winfax. Dll|
|WINHTTP. Dll|Wininet. Dll|WINMM. Dll|WINSCARD. Dll|
|WINTRUST. Dll|WLDAP32. Dll|WOW32. Dll|WS2_32.DLL|
|WSNMP32. Dll|WSOCK32.DLL|WTSAPI32. Dll|XOLEHLP. Dll|

> [!NOTE]
> Das Beibehalten des letzten Fehlers wird für nicht verwaltete Funktionen, die vom CLR-Code im selben Modul verwendet werden, nicht unterstützt.

- Weitere Informationen finden Sie unter [/clr (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **Linker**.

1. Klicken Sie auf die Eigenschaftenseite **Befehlszeile** .

1. Geben Sie die Option in das Feld **Zusätzliche Optionen** ein.

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird eine systemeigene DLL mit einer exportierten Funktion definiert, die den letzten Fehler ändert.

```cpp
// CLRSUPPORTLASTERROR_dll.cpp
// compile with: /LD
#include <windows.h>
#include <math.h>

#pragma unmanaged
__declspec(dllexport) double MySqrt(__int64 n) {
   SetLastError(DWORD(-1));
   return sqrt(double(n));
}
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die DLL verwendet und die Verwendung von **/CLRSUPPORTLASTERROR**veranschaulicht.

```cpp
// CLRSUPPORTLASTERROR_client.cpp
// compile with: /clr CLRSUPPORTLASTERROR_dll.lib /link /clrsupportlasterror:systemdll
// processor: x86
#include <windows.h>
#include <wininet.h>
#include <stdio.h>
#include <math.h>

#pragma comment(lib, "wininet.lib")

double MySqrt(__int64 n);

#pragma managed
int main() {
   double   d = 0.0;
   __int64 n = 65;
   HANDLE  hGroup = NULL;
   GROUPID groupID;
   DWORD   dwSet = 127, dwGet = 37;

   SetLastError(dwSet);
   d = MySqrt(n);
   dwGet = GetLastError();

   if (dwGet == DWORD(-1))
      printf_s("GetLastError for application call succeeded (%d).\n",
             dwGet);
   else
      printf_s("GetLastError for application call failed (%d).\n",
             dwGet);

   hGroup = FindFirstUrlCacheGroup(0, CACHEGROUP_SEARCH_ALL,
                           0, 0, &groupID, 0);
   dwGet = GetLastError();
   if (dwGet == 183)
      printf_s("GetLastError for system call succeeded (%d).\n",
             dwGet);
   else
      printf_s("GetLastError for system call failed (%d).\n",
             dwGet);
}
```

```Output
GetLastError for application call failed (127).
GetLastError for system call succeeded (183).
```

## <a name="see-also"></a>Siehe auch

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)
