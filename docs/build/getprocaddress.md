---
title: GetProcAddress
ms.date: 11/04/2016
f1_keywords:
- GetProcAddress
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
ms.openlocfilehash: 2d322cfe7d3bd60d8d702a226e181eb7b4ede963
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493254"
---
# <a name="getprocaddress"></a>GetProcAddress

Prozesse, die explizit mit einer DLL verknüpft werden, rufen [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) auf, um die Adresse einer exportierten Funktion in der DLL abzurufen. Sie rufen die DLL-Funktion dann über den zurückgegebenen Funktionszeiger auf. **GetProcAddress** verwendet als Parameter das (von **LoadLibrary**, `AfxLoadLibrary` oder **GetModuleHandle** zurückgegebene) DLL-Modulhandle sowie entweder den Namen der Funktion, die Sie aufrufen möchten, oder ihre Exportordnungszahl.

Da Sie die DLL-Funktion über einen Zeiger aufrufen und zur Kompilierungszeit keine Typüberprüfung erfolgt, sollten Sie sicherstellen, dass die Parameter für die Funktion korrekt sind, damit Sie nicht den auf dem Stapel belegten Speicherbereich überschreiten und eine Zugriffsverletzung verursachen. Eine Möglichkeit die Typsicherheit zu gewährleisten besteht darin, sich die Funktionsprototypen der exportierten Funktionen anzusehen und entsprechende Typdefinitionen für die Funktionszeiger zu erstellen. Zum Beispiel:

```
typedef UINT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT);
...

HINSTANCE hDLL;               // Handle to DLL
LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer
DWORD dwParam1;
UINT  uParam2, uReturnVal;

hDLL = LoadLibrary("MyDLL");
if (hDLL != NULL)
{
   lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL,
                                           "DLLFunc1");
   if (!lpfnDllFunc1)
   {
      // handle the error
      FreeLibrary(hDLL);
      return SOME_ERROR_CODE;
   }
   else
   {
      // call the function
      uReturnVal = lpfnDllFunc1(dwParam1, uParam2);
   }
}
```

Wie Sie die gewünschte Funktion beim Aufrufen von **GetProcAddress** angeben, hängt davon ab, wie die DLL erstellt wurde.

Sie können die Exportordnungszahl nur abrufen, wenn die zu verknüpfende DLL mithilfe einer Moduldefinitionsdatei (DEF-Datei) erstellt wurde und die Ordnungszahlen zusammen mit den Funktionen im **EXPORTS**-Abschnitt der DEF-Datei für die DLL aufgeführt sind. Wenn die DLL zahlreiche exportierte Funktionen aufweist, ist der Aufruf von **GetProcAddress** mit einer Exportordnungszahl geringfügig schneller als die Verwendung des Funktionsnamens, da die Exportordnungszahlen als Indizes für die Exporttabelle der DLL dienen. Mit einer Exportordnungszahl kann die Funktion von **GetProcAddress** direkt aufgespürt werden, und der angegebene Name muss nicht mit den Funktionsnamen in der Exporttabelle der DLL verglichen werden. Sie sollten **GetProcAddress** jedoch nur dann mit einer Exportordnungszahl aufrufen, wenn Sie die Zuordnung der Ordnungszahlen zu den exportierten Funktionen in der DEF-Datei steuern können.

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Link an executable to a DLL (Eine ausführbare Datei mit einer DLL verknüpfen)](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Link an executable to a DLL (Eine ausführbare Datei mit einer DLL verknüpfen)](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [LoadLibrary und AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)

- [Exportieren aus einer DLL mithilfe von DEF-Dateien](exporting-from-a-dll-using-def-files.md)

## <a name="see-also"></a>Siehe auch

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)
