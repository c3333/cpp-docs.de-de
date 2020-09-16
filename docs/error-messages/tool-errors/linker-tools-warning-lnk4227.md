---
title: Linkertoolwarnung LNK4227
ms.date: 11/04/2016
f1_keywords:
- LNK4227
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
ms.openlocfilehash: 7ac3ef2b6ad8f05a454dafe5e6a7ea0abc07a066
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685488"
---
# <a name="linker-tools-warning-lnk4227"></a>Linkertoolwarnung LNK4227

> Warnung zu Metadatenvorgang (*HRESULT*): *warning_message*

Der Linker hat bei der Zusammenführung metadatenunterschiede erkannt:

- Eine oder mehrere referenzierte Assemblys mit der Assembly, die gerade erstellt wird.

- Eine oder mehrere Quell Code Dateien in einer Kompilierung.

Beispielsweise kann Linkertoolwarnung LNK4227 auftreten, wenn Sie über zwei globale Funktionen mit demselben Namen verfügen, die Parameterinformationen jedoch unterschiedlich deklariert sind (d. h., Deklarationen sind nicht in allen Kompilierungen konsistent). Verwenden Sie ildasm.exe/Text/Metadata *object_file* in jeder OBJ-Datei, um zu sehen, wie sich die Typen unterscheiden.

Linkertoolwarnung LNK4227 wird auch verwendet, um Probleme zu melden, die von einem anderen Tool stammen. Suchen Sie nach der Warnmeldung, um weitere Informationen zu finden.

Die metadatenprobleme müssen korrigiert werden, um die Warnung zu beheben.

## <a name="examples"></a>Beispiele

Linkertoolwarnung LNK4227 wird generiert, wenn eine Assembly, auf die verwiesen wird, anders signiert wurde als die Assembly, die darauf verweist.

Im folgenden Beispiel wird Linkertoolwarnung LNK4227 generiert:

```cpp
// LNK4227.cpp
// compile with: /clr
using namespace System::Reflection;

[assembly:AssemblyDelaySignAttribute(false)];

int main() {}
```

Und dann

```cpp
// LNK4227b.cpp
// compile with: /clr LNK4227.cpp /FeLNK4227b.exe
using namespace System::Reflection;
using namespace System::Runtime::CompilerServices;

[assembly:AssemblyDelaySignAttribute(true)];
// Try the following line instead
// [assembly:AssemblyDelaySignAttribute(false)];

ref class MyClass
{
};
```

Linkertoolwarnung LNK4227 kann auch generiert werden, wenn Versionsnummern im falschen Format an Assemblyattribute übermittelt werden.  Die *-Notation ist für spezifisch `AssemblyVersionAttribute` .  Um diese Warnung zu beheben, verwenden Sie nur Zahlen in den Versions Attributen, die nicht sind `AssemblyVersionAttribute` .

Im folgenden Beispiel wird Linkertoolwarnung LNK4227 generiert:

```cpp
// LNK4227e.cpp
// compile with: /clr /LD /W1
using namespace System::Reflection;
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227
// try the following line instead
// [assembly:AssemblyFileVersionAttribute("2.3")];
```
