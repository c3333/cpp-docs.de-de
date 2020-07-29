---
title: Entladen einer verzögert geladenen DLL
ms.date: 11/04/2016
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
ms.openlocfilehash: 1895bf12cb195ef7b4555d400badf112d377547b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211917"
---
# <a name="unloading-a-delay-loaded-dll"></a>Entladen einer verzögert geladenen DLL

Das standardmäßig bereitgestellte Hilfsprogramm für verzögertes Laden prüft, ob die Deskriptoren für verzögertes Laden über einen Zeiger und eine Kopie der ursprünglichen Import Adress Tabelle (IAT) im Feld pUnloadIAT verfügen. Wenn dies der Fall ist, wird ein Zeiger in einer Liste in den Deskriptor für die Import Verzögerung gespeichert. Dies ermöglicht der Hilfsfunktion, die DLL anhand des Namens zu finden, um das explizite Entladen der dll zu unterstützen.

Im folgenden sind die zugeordneten Strukturen und Funktionen zum expliziten Entladen einer verzögert geladenen DLL aufgeführt:

```cpp
//
// Unload support from delayimp.h
//

// routine definition; takes a pointer to a name to unload

ExternC
BOOL WINAPI
__FUnloadDelayLoadedDLL2(LPCSTR szDll);

// structure definitions for the list of unload records
typedef struct UnloadInfo * PUnloadInfo;
typedef struct UnloadInfo {
    PUnloadInfo     puiNext;
    PCImgDelayDescr pidd;
    } UnloadInfo;

// from delayhlp.cpp
// the default delay load helper places the unloadinfo records in the
// list headed by the following pointer.
ExternC
PUnloadInfo __puiHead;
```

Die UnloadInfo-Struktur wird mit einer C++-Klasse implementiert, die **localzuc** -und **LocalFree** -Implementierungen als Operator **`new`** und Operator verwendet **`delete`** . Diese Optionen werden in einer Standard verknüpften Liste gespeichert, wobei __puiHead als Anfang der Liste verwendet wird.

Wenn Sie __FUnloadDelayLoadedDLL aufrufen, wird versucht, den von Ihnen bereitgestellten Namen in der Liste der geladenen DLLs zu finden (eine genaue Entsprechung ist erforderlich). Wenn Sie gefunden wird, wird die Kopie von IAT in pUnloadIAT über den oberen Rand des ausgefallenen IAT kopiert, um die Thunk-Zeiger wiederherzustellen, die Bibliothek wird mit **FreeLibrary**freigegeben, die Verknüpfung des entsprechenden **UnloadInfo** -Datensatzes in der Liste wird aufgehoben, und true wird zurückgegeben.

Beim Argument für die Funktion __FUnloadDelayLoadedDLL2 wird die Groß-/Kleinschreibung beachtet. Beispielsweise würden Sie Folgendes angeben:

```cpp
__FUnloadDelayLoadedDLL2("user32.DLL");
```

und nicht:

```cpp
__FUnloadDelayLoadedDLL2("User32.DLL");.
```

## <a name="see-also"></a>Weitere Informationen

[Grundlegendes zur Hilfsfunktion](understanding-the-helper-function.md)
