---
title: Automatisierung in einer DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: dedc832d6726dccf8c0c2e88f9f4d5c67590c1c2
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220921"
---
# <a name="automation-in-a-dll"></a>Automatisierung in einer DLL

Wenn Sie die Automatisierungsoption im MFC-DLL-Assistent auswählen, stellt Ihnen der Assistent Folgendes bereit:

- Eine Object Description Language-Datei (.ODL) für den Start

- Eine include-Anweisung in der STDAFX.h-Datei für Afxole.h

- Eine Implementierung der `DllGetClassObject`-Funktion, die die Funktion **AfxDllGetClassObject** aufruft

- Eine Implementierung der `DllCanUnloadNow`-Funktion, die die Funktion **AfxDllCanUnloadNow** aufruft

- Eine Implementierung der `DllRegisterServer`-Funktion, die die Funktion [COleObjectFactory::UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall) aufruft

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Automatisierungsserver](../mfc/automation-servers.md)

## <a name="see-also"></a>Siehe auch

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)
