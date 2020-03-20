---
title: Namespaces „Platform“, „default“ und „cli“ (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- lang
- cli
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
ms.openlocfilehash: db6c73d6c52bf97aea5d0fbeeeebdeef87f692cc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544651"
---
# <a name="platform-default-and-cli-namespaces--ccli-and-ccx"></a>Namespaces „Platform“, „default“ und „cli“ (C++/CLI und C++/CX)

Ein Namespace qualifiziert die Namen von Sprachelementen, sodass sie keinen Konflikt mit ansonsten identischen Namen an anderer Stelle im Quellcode verursachen. Beispielsweise kann ein Namenskonflikt verhindern, dass der Compiler [kontextbezogene Schlüsselwörter](context-sensitive-keywords-cpp-component-extensions.md) erkennt. Namespaces werden vom Compiler verwendet, jedoch nicht in der kompilierten Assembly beibehalten.

## <a name="all-runtimes"></a>Alle Laufzeiten

Beim Erstellen des Projekts stellt Visual Studio einen Standardnamespace für das Projekt bereit. Sie können den Namespace manuell umbenennen, obwohl der Name der WINMD-Datei in C++/CX mit dem Namen des Stammnamespace übereinstimmen muss.

## <a name="windows-runtime"></a>Windows-Runtime

Weitere Informationen finden Sie unter [Namespaces und Typsichtbarkeit (C++/CX)](../cppcx/namespaces-and-type-visibility-c-cx.md).

### <a name="requirements"></a>Voraussetzungen

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>Syntax

```cpp
using namespace cli;
```

### <a name="remarks"></a>Hinweise

C++/CLI unterstützt den Namespace **cli**. Beim Kompilieren mit `/clr` ist die **using**-Anweisung im Syntaxabschnitt impliziert.

Im Namespace **cli** befinden sich die folgenden Sprachfeatures:

- [Arrays](arrays-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)

- [pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)

- [safe_cast](safe-cast-cpp-component-extensions.md)

### <a name="requirements"></a>Voraussetzungen

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Das folgende Codebeispiel veranschaulicht, dass es möglich ist, ein Symbol im **cli**-Namespace als benutzerdefiniertes Symbol im Code zu verwenden.  Sobald dies geschehen ist, müssen Sie die Verweise auf das **cli**-Sprachelement des gleichen Namens jedoch explizit oder implizit qualifizieren.

```cpp
// cli_namespace.cpp
// compile with: /clr
using namespace cli;
int main() {
   array<int> ^ MyArray = gcnew array<int>(100);
   int array = 0;

   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062

   // OK
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);
}
```

## <a name="see-also"></a>Siehe auch

[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)