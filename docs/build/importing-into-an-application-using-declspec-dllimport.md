---
title: Importieren in eine Anwendung mithilfe von __declspec(dllimport)
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
ms.openlocfilehash: 50b630334cfd8752935b54549190d698fa5136bb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223979"
---
# <a name="import-into-an-application-using-__declspecdllimport"></a>Importieren in eine Anwendung mithilfe von __declspec(dllimport)

Wenn ein Programm öffentliche, durch eine DLL definierte Symbole verwendet, wird dieser Vorgang als Importieren bezeichnet. Wenn Sie Headerdateien für Anwendungen erstellen, die Ihre DLLs zum Kompilieren verwenden, sollten Sie für die Deklarationen der öffentlichen Symbole **`__declspec(dllimport)`** verwenden. Das Schlüsselwort **`__declspec(dllimport)`** funktioniert unabhängig davon, ob Sie DEF-Dateien oder das Schlüsselwort **`__declspec(dllexport)`** für den Export verwenden.

Definieren Sie ein Makro für **`__declspec(dllimport)`** , und verwenden Sie dieses zur Deklaration aller importierten Symbole, um den Code lesbarer zu gestalten:

```
#define DllImport   __declspec( dllimport )

DllImport int  j;
DllImport void func();
```

Die Verwendung von **`__declspec(dllimport)`** ist bei Funktionsdeklarationen optional, der Compiler generiert jedoch effizienteren Code, wenn Sie dieses Schlüsselwort verwenden. **`__declspec(dllimport)`** muss jedoch verwendet werden, damit die importierende ausführbare Datei auf die öffentlichen Datensymbole und Objekte der DLL zugreifen kann. Beachten Sie, dass die Benutzer Ihrer DLL noch eine Verknüpfung mit einer Importbibliothek herstellen müssen.

Sie können dieselbe Headerdatei sowohl für die DLL als auch für die Clientanwendung nutzen. Verwenden Sie zu diesem Zweck ein spezielles Präprozessorsymbol, das angibt, ob die DLL oder die Clientanwendung erstellt wird. Zum Beispiel:

```
#ifdef _EXPORTING
   #define CLASS_DECLSPEC    __declspec(dllexport)
#else
   #define CLASS_DECLSPEC    __declspec(dllimport)
#endif

class CLASS_DECLSPEC CExampleA : public CObject
{ ... class definition ... };
```

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Initialisieren einer DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Importieren und Exportieren von Inlinefunktionen](importing-and-exporting-inline-functions.md)

- [Gegenseitige Importe](mutual-imports.md)

## <a name="see-also"></a>Siehe auch

[Importieren in eine Anwendung](importing-into-an-application.md)
