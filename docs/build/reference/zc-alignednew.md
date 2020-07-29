---
title: /Zc:alignedNew (C++17-Zuteilung mit erweiterter Ausrichtung)
ms.date: 05/18/2019
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: f036c2d7bc4619685d2763702f447476e8e1a1e4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217193"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew (C++17-Zuteilung mit erweiterter Ausrichtung)

Aktivieren Sie die Unterstützung für "c++ 17 over-align" **`new`** , die dynamische Speicher Belegung, die auf Grenzen ausgerichtet **ist, \_ \_ **die größer als der Standardwert für den standardmäßigen ausgerichteten Standardtyp ist.

## <a name="syntax"></a>Syntax

> **/Zc: alignednew** \[ -]

## <a name="remarks"></a>Bemerkungen

Der MSVC-Compiler und die -Bibliothek unterstützten die dynamische Speicherzuteilung für C++17 mit erweiterter Ausrichtung. Wenn die **/Zc: alignednew** -Option angegeben ist, wird bei einer dynamischen Zuordnung, wie z. b. `new Example;` die Ausrichtung von *Beispielen* , auch wenn Sie größer als ist `max_align_t` , die größte Ausrichtung für einen grundlegenden Typ berücksichtigt. Wenn die Ausrichtung des zugeordneten Typs nicht länger ist als die durch den ursprünglichen Operator garantierte Ausrichtung **`new`** , die als Wert für die vordefinierte standardmäßige " ** \_ \_ stdcpp"- \_ Standard \_ \_ \_ \_ Ausrichtung**verfügbar ist, führt die-Anweisung `new Example;` zu einem-Aufrufvorgang `::operator new(size_t)` wie in c++ 14. Wenn die Ausrichtung größer als die ** \_ \_ \_ standardmäßige Standard \_ \_ \_ \_ Ausrichtung stdcpp**ist, ruft die-Implementierung den Speicher mithilfe von ab `::operator new(size_t, align_val_t)` . Ebenso werden `::operator delete(void*, align_val_t)` oder die Löschsignatur mit angegebener Größe (`::operator delete(void*, size_t, align_val_t)`) aufgerufen, wenn Typen mit erweiterter Ausrichtung gelöscht werden.

Die Option **/Zc:alignedNew** ist nur verfügbar, wenn [/std:c++17](std-specify-language-standard-version.md) oder [/std:c++latest](std-specify-language-standard-version.md) aktiviert ist. Unter **/std:c++17** oder **/std:c++latest** wird gemäß dem ISO-Standard für C++17 standardmäßig **/Zc:alignedNew** aktiviert. Wenn Sie den einzigen Grund für die Implementierung des Operators **`new`** und die **`delete`** Unterstützung von über ausgerichteten Zuordnungen benötigen, benötigen Sie diesen Code möglicherweise nicht mehr im c++ 17-Modus. Um diese Option zu deaktivieren und zum c++ 14-Verhalten von und zurückzukehren, **`new`** **`delete`** Wenn Sie **/Std:: c++ 17** oder **/Std: C + + Latest**verwenden, geben Sie **/Zc: alignednew-** an. Wenn Sie **`new`** den-Operator implementieren und **`delete`** Sie nicht bereit sind, den über ausgerichteten Operator **`new`** und **`delete`** über Ladungen mit dem-Parameter zu implementieren `align_val_t` , verwenden Sie die Option **/Zc: alignednew-** , um zu verhindern, dass der Compiler und die Standard Bibliothek Aufrufe der über-ausgerichteten über Ladungen erzeugen. Die Standardeinstellung von **/Zc:alignedNew** wird durch die Option [/permissive-](permissive-standards-conformance.md) nicht geändert.

**/Zc:alignedNew** wird ab Visual Studio 2017, Version 15.5 unterstützt.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie **`new`** sich Operator und Operator **`delete`** Verhalten, wenn die Option **/Zc: alignednew** festgelegt ist.

```cpp
// alignedNew.cpp
// Compile by using: cl /EHsc /std:c++17 /W4 alignedNew.cpp
#include <iostream>
#include <malloc.h>
#include <new>

// "old" unaligned overloads
void* operator new(std::size_t size) {
    auto ptr = malloc(size);
    std::cout << "unaligned new(" << size << ") = " << ptr << '\n';
    return ptr ? ptr : throw std::bad_alloc{};
}

void operator delete(void* ptr, std::size_t size) {
    std::cout << "unaligned sized delete(" << ptr << ", " << size << ")\n";
    free(ptr);
}

void operator delete(void* ptr) {
    std::cout << "unaligned unsized delete(" << ptr << ")\n";
    free(ptr);
}

// "new" over-aligned overloads
void* operator new(std::size_t size, std::align_val_t align) {
    auto ptr = _aligned_malloc(size, static_cast<std::size_t>(align));
    std::cout << "aligned new(" << size << ", " <<
        static_cast<std::size_t>(align) << ") = " << ptr << '\n';
    return ptr ? ptr : throw std::bad_alloc{};
}

void operator delete(void* ptr, std::size_t size, std::align_val_t align) {
    std::cout << "aligned sized delete(" << ptr << ", " << size <<
        ", " << static_cast<std::size_t>(align) << ")\n";
    _aligned_free(ptr);
}

void operator delete(void* ptr, std::align_val_t align) {
    std::cout << "aligned unsized delete(" << ptr <<
        ", " << static_cast<std::size_t>(align) << ")\n";
    _aligned_free(ptr);
}

struct alignas(256) OverAligned {}; // warning C4324, structure is padded

int main() {
    delete new int;
    delete new OverAligned;
}
```

Diese Ausgabe ist typisch für 32-Bit-Builds. Die Zeigerwerte variieren je nach Ausführungsort Ihrer Anwendung im Speicher.

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Weitere Informationen über Konformitätsprobleme in Visual C++ finden Sie unter [Nicht dem Standard entsprechendes Verhalten](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Ändern Sie die Eigenschaft **Weitere Optionen**, um **/Zc:alignedNew** oder **/Zc:alignedNew-** hinzuzufügen, und klicken Sie dann auf **OK**.

## <a name="see-also"></a>Weitere Informationen

[/Zc (Übereinstimmung)](zc-conformance.md)
