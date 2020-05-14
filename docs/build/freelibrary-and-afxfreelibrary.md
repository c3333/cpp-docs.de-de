---
title: "\"FreeLibrary\" und \"AfxFreeLibrary\""
ms.date: 11/04/2016
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
ms.openlocfilehash: 0b530aca2ab036de186ff3fdb11be23f41e12d05
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821550"
---
# <a name="freelibrary-and-afxfreelibrary"></a>"FreeLibrary" und "AfxFreeLibrary"

Prozesse, die explizit eine Verknüpfung zu einer DLL herstellen und die [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)-Funktion aufrufen, wenn das DLL-Modul nicht mehr benötigt wird. Diese Funktion dekrementiert die Verweisanzahl des Moduls. Wenn die Verweisanzahl 0 (Null) ist, wird die Zuordnung für den Adressraum des Prozesses aufgehoben.

Verwenden Sie in einer MFC-Anwendung [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) anstelle von `FreeLibrary`, um eine Erweiterungs-DLL für MFC zu entladen. Die Schnittstelle (Funktionsprototyp) für `AfxFreeLibrary` ist mit `FreeLibrary` identisch.

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Link an executable to a DLL (Eine ausführbare Datei mit einer DLL verknüpfen)](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Link an executable to a DLL (Eine ausführbare Datei mit einer DLL verknüpfen)](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [LoadLibrary und AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Siehe auch

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)\
[FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)\
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)
