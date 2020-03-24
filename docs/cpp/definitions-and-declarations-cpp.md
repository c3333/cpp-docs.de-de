---
title: Definitionen und Deklarationen (C++)
ms.date: 11/04/2016
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
ms.openlocfilehash: 20683f3d2e12f7ffead573cbac46fdd4e106c383
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189376"
---
# <a name="definitions-and-declarations-c"></a>Definitionen und Deklarationen (C++)

**Microsoft-spezifisch**

Die DLL-Schnittstelle bezieht sich auf alle Elemente (Funktionen und Daten), von denen bekannt ist, dass Sie von einem Programm im System exportiert werden. Das heißt, alle Elemente, die als **DllImport** oder **dllexport**deklariert werden. Alle Deklarationen, die in der DLL-Schnittstelle enthalten sind, müssen das **DllImport** -oder **dllexport** -Attribut angeben. Allerdings muss in der Definition nur das **dllexport** -Attribut angegeben werden. Beispielsweise verursacht die folgende Funktionsdefinition einen Compilerfehler:

```
__declspec( dllimport ) int func() {   // Error; dllimport
                                       // prohibited on definition.
   return 1;
}
```

Dieser Code generiert außerdem einen Fehler:

```
__declspec( dllimport ) int i = 10;  // Error; this is a definition.
```

Dies ist jedoch die richtige Syntax:

```
__declspec( dllexport ) int i = 10;  // Okay--export definition
```

Die Verwendung von **dllexport** impliziert eine Definition, während **DllImport** eine Deklaration impliziert. Sie müssen das **extern** -Schlüsselwort mit **dllexport** verwenden, um eine Deklaration zu erzwingen. Andernfalls wird eine Definition impliziert. Daher sind die folgenden Beispiele richtig:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllExport int k; // These are both correct and imply a
DllImport int j;        // declaration.
```

Das vorherige Beispiel wird anhand der folgenden Beispiele verdeutlicht:

```
static __declspec( dllimport ) int l; // Error; not declared extern.

void func() {
    static __declspec( dllimport ) int s;  // Error; not declared
                                           // extern.
    __declspec( dllimport ) int m;         // Okay; this is a
                                           // declaration.
    __declspec( dllexport ) int n;         // Error; implies external
                                           // definition in local scope.
    extern __declspec( dllimport ) int i;  // Okay; this is a
                                           // declaration.
    extern __declspec( dllexport ) int k;  // Okay; extern implies
                                           // declaration.
    __declspec( dllexport ) int x = 5;     // Error; implies external
                                           // definition in local scope.
}
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
