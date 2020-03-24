---
title: Kontextbezogene Schlüsselwörter (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- internal_CPP
helpviewer_keywords:
- context-sensitive keywords
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
ms.openlocfilehash: 53fcaf13eb56ae14841861bffd1a29376304b8d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182174"
---
# <a name="context-sensitive-keywords--ccli-and-ccx"></a>Kontextbezogene Schlüsselwörter (C++/CLI und C++/CX)

*Kontextbezogene Schlüsselwörter* sind Sprachelemente, die nur in bestimmten Kontexten erkannt werden. Außerhalb des jeweiligen Kontexts kann ein kontextbezogenes Schlüsselwort ein benutzerdefiniertes Symbol sein.

## <a name="all-runtimes"></a>Alle Laufzeiten

### <a name="remarks"></a>Bemerkungen

Die folgende Liste enthält die kontextbezogenen Schlüsselwörter:

- [abstract](abstract-cpp-component-extensions.md)

- [delegate](delegate-cpp-component-extensions.md)

- [event](event-cpp-component-extensions.md)

- [finally](../dotnet/finally.md)

- [for each in](../dotnet/for-each-in.md)

- [initonly](../dotnet/initonly-cpp-cli.md)

- `internal`

- [literal](literal-cpp-component-extensions.md)

- [override](override-cpp-component-extensions.md)

- [property](property-cpp-component-extensions.md)

- [sealed](sealed-cpp-component-extensions.md)

- `where` (Teil von [Generics](generics-cpp-component-extensions.md))

Um die Lesbarkeit zu erhöhen, sollten Sie die Verwendung von kontextbezogenen Schlüsselwörtern als benutzerdefinierte Symbole einschränken.

## <a name="windows-runtime"></a>Windows-Runtime

### <a name="remarks"></a>Bemerkungen

(Es gibt keine plattformspezifischen Hinweise für diese Funktion.)

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Bemerkungen

(Es gibt keine plattformspezifischen Hinweise für diese Funktion.)

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Im folgenden Codebeispiel wird dargestellt, wie das kontextbezogene Schlüsselwort **property** im entsprechenden Kontext verwendet werden kann, um eine Eigenschaft und eine Variable zu definieren.

```cpp
// context_sensitive_keywords.cpp
// compile with: /clr
public ref class C {
   int MyInt;
public:
   C() : MyInt(99) {}

   property int Property_Block {   // context-sensitive keyword
      int get() { return MyInt; }
   }
};

int main() {
   int property = 0;               // variable name
   C ^ MyC = gcnew C();
   property = MyC->Property_Block;
   System::Console::WriteLine(++property);
}
```

```Output
100
```

## <a name="see-also"></a>Weitere Informationen

[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)
