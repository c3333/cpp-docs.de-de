---
title: pack-Pragma
ms.date: 07/22/2020
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: 72f94520516cce2ae36b70795fb29e3d4d8068df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219390"
---
# <a name="pack-pragma"></a>pack-Pragma

Gibt die Verpackungs Ausrichtung für Struktur-, Union-und Klassenmember an.

## <a name="syntax"></a>Syntax

> **`#pragma pack( show )`**\
> **`#pragma pack( push`** [ **`,`** *`identifier`* ] [ **`,`** *`n`* ] **`)`**\
> **`#pragma pack( pop`** [ **`,`** { *`identifier`* | *`n`* } ] **`)`**\
> **`#pragma pack(`** [ *`n`* ] **`)`**

### <a name="parameters"></a>Parameter

**`show`**\
Optionale Zeigt den aktuellen Bytewert für die Verpackungs Ausrichtung an. Der Wert wird von einer Warnmeldung angezeigt.

**`push`**\
Optionale Überträgt den aktuellen Verpackungs Ausrichtungs Wert auf den internen compilerstapel und legt den aktuellen Verpackungs Ausrichtungs Wert auf *n*fest. Wenn *n* nicht angegeben ist, wird der aktuelle Wert für die Verpackungs Ausrichtung per pushübertragung übermittelt

**`pop`**\
Optionale Entfernt den Datensatz von der obersten Position des internen Compilerstapels. Wenn *n* nicht mit angegeben ist **`pop`** , ist der Verpackungs Wert, der dem resultierenden Datensatz am oberen Rand des Stapels zugeordnet ist, der neue Verpackungs Ausrichtungs Wert. Wenn *n* angegeben wird, z. b `#pragma pack(pop, 16)` ., wird *n* zum neuen Verpackungs Ausrichtungs Wert. Wenn Sie z. b. mit einem mit einem Pop (z. b.) verwenden, *`identifier`* `#pragma pack(pop, r1)` werden alle Datensätze auf dem Stapel bis zum gefundenen Datensatz per Pop weitergeleitet *`identifier`* . Dieser Datensatz wird abgerufen, und der Verpackungs Wert, der dem Datensatz am oberen Rand des Stapels zugeordnet ist, wird zum neuen Verpackungs Ausrichtungs Wert. Wenn Sie mit einem-Wert verwenden, *`identifier`* der nicht in einem Datensatz auf dem Stapel gefunden wird, **`pop`** wird der ignoriert.

Die-Anweisung `#pragma pack (pop, r1, 2)` entspricht, `#pragma pack (pop, r1)` gefolgt von `#pragma pack(2)` .

*`identifier`*\
Optionale Bei Verwendung mit **`push`** weist dem Datensatz im internen compilerstapel einen Namen zu. Bei Verwendung mit werden **`pop`** Datensätze vom internen Stapel bis zum *`identifier`* Entfernen von angezeigt. Wenn *`identifier`* auf dem internen Stapel nicht gefunden wird, wird nichts weitergeleitet.

*`n`*\
Optionale Gibt den Wert in Bytes an, der für das Packen verwendet werden soll. Wenn die Compileroption [`/Zp`](../build/reference/zp-struct-member-alignment.md) für das Modul nicht festgelegt ist, ist der Standardwert für *`n`* 8. Gültige Werte sind 1, 2, 4, 8 und 16. Die Ausrichtung eines Members erfolgt an einer Begrenzung, bei der es sich entweder um ein Vielfaches von *`n`* oder um ein Vielfaches der Größe des Members handelt, je nachdem, welcher Wert kleiner ist.

## <a name="remarks"></a>Bemerkungen

Um eine Klasse zu *Verpacken* , müssen Sie die zugehörigen Member direkt im Arbeitsspeicher platzieren. Dies kann bedeuten, dass einige oder alle Elemente an einer Grenze ausgerichtet werden können, die kleiner als die Standardausrichtung der Zielarchitektur ist. **`pack`** übergibt die Steuerung auf der Ebene der Daten Deklaration. Dies unterscheidet sich von der Compileroption [`/Zp`](../build/reference/zp-struct-member-alignment.md) , die nur Steuerelemente auf Modulebene bereitstellt. **Pack** wird bei der ersten- **`struct`** ,- **`union`** oder-Deklaration wirksam, **`class`** nachdem das Pragma sichtbar ist. **`pack`** hat keine Auswirkung auf Definitionen. **`pack`** Der Aufruf von ohne Argumente legt *`n`* auf den in der Compileroption festgelegten Wert fest **`/Zp`** . Wenn die-Compileroption nicht festgelegt ist, ist der Standardwert 8 für x86, Arm und ARM64. Der Standardwert ist 16 für x64 Native.

Wenn Sie die Ausrichtung einer Struktur ändern, wird möglicherweise nicht so viel Speicherplatz im Arbeitsspeicher verwendet. Möglicherweise wird jedoch ein Leistungsverlust oder sogar eine Hardware generierte Ausnahme für den nicht ausgerichteten Zugriff angezeigt. Sie können dieses Ausnahme Verhalten mithilfe von ändern [`SetErrorMode`](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) .

Weitere Informationen zum Ändern der Ausrichtung finden Sie in den folgenden Artikeln:

- [`alignof`](../cpp/alignof-operator.md)

- [`align`](../cpp/align-cpp.md)

- [`__unaligned`](../cpp/unaligned.md)

- [Beispiele für die Struktur Ausrichtung](../build/x64-software-conventions.md#examples-of-structure-alignment) (x64-spezifisch)

   > [!WARNING]
   > In Visual Studio 2015 und höher können Sie die Standard **`alignas`** -und- **`alignof`** Operatoren verwenden, die im Gegensatz zu **`__alignof`** und **`__declspec( align )`** über Compiler hinweg portabel sind. Da der C++-Standard keine Komprimierung adressiert, müssen Sie immer noch **`pack`** (oder die entsprechende Erweiterung auf anderen Compilern) verwenden, um Ausrichtungen anzugeben, die kleiner als die Wort Größe der Zielarchitektur sind.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird gezeigt, wie das- **`pack`** pragma verwendet wird, um die Ausrichtung einer Struktur zu ändern.

```cpp
// pragma_directives_pack.cpp
#include <stddef.h>
#include <stdio.h>

struct S {
   int i;   // size 4
   short j;   // size 2
   double k;   // size 8
};

#pragma pack(2)
struct T {
   int i;
   short j;
   double k;
};

int main() {
   printf("%zu ", offsetof(S, i));
   printf("%zu ", offsetof(S, j));
   printf("%zu\n", offsetof(S, k));

   printf("%zu ", offsetof(T, i));
   printf("%zu ", offsetof(T, j));
   printf("%zu\n", offsetof(T, k));
}
```

```Output
0 4 8
0 4 6
```

Das folgende Beispiel zeigt die Verwendung der *Push*-, *Pop*-und *Show* -Syntax.

```cpp
// pragma_directives_pack_2.cpp
// compile with: /W1 /c
#pragma pack()   // n defaults to 8; equivalent to /Zp8
#pragma pack(show)   // C4810
#pragma pack(4)   // n = 4
#pragma pack(show)   // C4810
#pragma pack(push, r1, 16)   // n = 16, pushed to stack
#pragma pack(show)   // C4810

// pop to the identifier and then set
// the value of the current packing alignment:
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>Weitere Informationen

[Pragma-Direktiven und das `__pragma` Schlüsselwort](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
