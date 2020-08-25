---
title: /CLRSUPPORTLASTERROR (Letzten Fehlercode für PInvoke-Aufrufe beibehalten)
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: 071846e18dfef6cad0b7c5fb983dac3f6c85a689
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839165"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (Letzten Fehlercode für PInvoke-Aufrufe beibehalten)

**/CLRSUPPORTLASTERROR**, das standardmäßig aktiviert ist, behält den letzten Fehlercode von Funktionen bei, die durch den P/Aufruf-Mechanismus aufgerufen werden. Dadurch können Sie Native Funktionen in DLLs aufrufen, von mit **/CLR**kompilierten Code.

## <a name="syntax"></a>Syntax

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>Bemerkungen

Die Beibehaltung des letzten Fehlercodes impliziert eine Abnahme der Leistung.  Wenn Sie keine Auswirkungen auf die Leistung bei der Beibehaltung des letzten Fehlercodes haben möchten, verknüpfen Sie mit  **/CLRSUPPORTLASTERROR: No**.

Sie können die Auswirkungen auf die Leistung minimieren, indem Sie eine Verknüpfung mit **/CLRSUPPORTLASTERROR: SYSTEMDLL**herstellen, die nur den letzten Fehlercode für Funktionen in System-DLLs beibehält.

> [!NOTE]
> Die Beibehaltung des letzten Fehlers wird nicht für nicht verwaltete Funktionen unterstützt, die von CLR-Code im selben Modul genutzt werden.

- Weitere Informationen finden Sie unter [/CLR (Common Language Runtime-Kompilierung)](clr-common-language-runtime-compilation.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **Linker**.

1. Klicken Sie auf die Eigenschaftenseite **Befehlszeile** .

1. Geben Sie die Option im Feld **zusätzliche Optionen** ein.

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird eine native dll mit einer exportierten Funktion definiert, die den letzten Fehler ändert.

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

Im folgenden Beispiel wird die dll verwendet, und es wird gezeigt, wie **/CLRSUPPORTLASTERROR**verwendet wird.

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

## <a name="see-also"></a>Weitere Informationen

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)
