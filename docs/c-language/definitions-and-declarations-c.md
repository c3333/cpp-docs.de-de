---
title: Definitionen und Deklarationen (C)
ms.date: 11/04/2016
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
ms.openlocfilehash: 0e39832f942eb1473be913112fde1d37ddf05674
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226365"
---
# <a name="definitions-and-declarations-c"></a>Definitionen und Deklarationen (C)

**Microsoft-spezifisch**

Die DLL-Schnittstelle bezieht sich auf alle Elemente (Funktionen und Daten), von denen bekannt ist, dass sie von einem Programm im System exportiert werden, also alle als **`dllimport`** oder `dllexport` deklarierten Elemente. Bei allen Deklarationen, auf die sich die DLL-Schnittstelle bezieht, muss entweder das **`dllimport`** - oder das `dllexport`-Attribut angegeben sein. Allerdings kann die Definition nur das `dllexport`-Attribut angeben. Beispielsweise verursacht die folgende Funktionsdefinition einen Compilerfehler:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int func()    /* Error; dllimport prohibited in */
                        /* definition. */
{
   return 1;
}
```

Dieser Code generiert außerdem einen Fehler:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int i = 10;      /* Error; this is a definition. */
```

Dies ist jedoch die richtige Syntax:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport int i = 10;      /* Okay: this is an export definition. */
```

Die Verwendung von `dllexport` setzt eine Definition voraus, die von **`dllimport`** eine Deklaration. Sie müssen das **`extern`** -Schlüsselwort mit `dllexport` verwenden, um eine Deklaration zu erzwingen; andernfalls wird eine Definition vorausgesetzt.

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllImport int k;   /* These are correct and imply */
Dllimport int j;          /* a declaration. */
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Import- und Exportfunktionen einer DLL](../c-language/dll-import-and-export-functions.md)
