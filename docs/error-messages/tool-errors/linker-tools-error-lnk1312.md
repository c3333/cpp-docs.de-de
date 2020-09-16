---
title: Linkertoolfehler LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: 69af2bd2c22fdb1188cf0b7119791e451e80f966
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686495"
---
# <a name="linker-tools-error-lnk1312"></a>Linkertoolfehler LNK1312

Ungültige oder beschädigte Datei: die Assembly kann nicht importiert werden.

Beim Erstellen einer Assembly wurde eine andere Datei als ein Modul oder eine Assembly, die mit **/CLR** kompiliert wurde, an die **/ASSEMBLYMODULE** Linker-Option übermittelt.  Wenn Sie eine Objektdatei an **/ASSEMBLYMODULE**übergeben haben, übergeben Sie das Objekt einfach direkt an den Linker anstatt an **/ASSEMBLYMODULE**.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wurde die OBJ-Datei erstellt.

```cpp
// LNK1312.cpp
// compile with: /clr /LD
public ref class A {
public:
   int i;
};
```

Im folgenden Beispiel wird Linkertoolfehler LNK1312 generiert.

```cpp
// LNK1312_b.cpp
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj
// LNK1312 error expected
public ref class M {};
```
