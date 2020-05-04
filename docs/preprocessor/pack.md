---
title: pack-Pragma
ms.date: 11/11/2019
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: 037c57a10b1de7dd00249ae60acaef0939e355eb
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765733"
---
# <a name="pack-pragma"></a>pack-Pragma

Gibt die Verpackungs Ausrichtung für Struktur-, Union-und Klassenmember an.

## <a name="syntax"></a>Syntax

> **#Pragma Pack (anzeigen)**\
> **#pragma pack (Push** [ **,** *Bezeichner* ] [ **,** *n* ] **)**\
> **#pragma pack (Pop** [ **,** { *Identifier* | *n* }] **)**\
> **#pragma pack (** [ *n* ] **)**

### <a name="parameters"></a>Parameter

**auftritt**\
Optionale Zeigt den aktuellen Bytewert für die Verpackungs Ausrichtung an. Der Wert wird von einer Warnmeldung angezeigt.

**Push**\
Optionale Überträgt den aktuellen Verpackungs Ausrichtungs Wert auf den internen compilerstapel und legt den aktuellen Verpackungs Ausrichtungs Wert auf *n*fest. Wenn *n* nicht angegeben ist, wird der aktuelle Wert für die Verpackungs Ausrichtung per pushübertragung übermittelt

**Chor**\
Optionale Entfernt den Datensatz von der obersten Position des internen Compilerstapels. Wenn *n* nicht mit **Pop**angegeben wird, ist der Verpackungs Wert, der dem resultierenden Datensatz oben auf dem Stapel zugeordnet ist, der neue Verpackungs Ausrichtungs Wert. Wenn *n* angegeben wird, z `#pragma pack(pop, 16)`. b., wird *n* zum neuen Verpackungs Ausrichtungs Wert. Wenn Sie einen *Bezeichner*verwenden, z `#pragma pack(pop, r1)`. b., werden alle Datensätze auf dem Stapel so lange per Pop ausgeblendet, bis der Datensatz mit dem *Bezeichner* gefunden wurde. Dieser Datensatz wird per Pop ausgeblendet, und der Verpackungs Wert, der dem resultierenden Datensatz am oberen Rand des Stapels zugeordnet ist, ist der neue Verpackungs Ausrichtungs Wert. Wenn Sie einen *Bezeichner* verwenden, der nicht in einem Datensatz auf dem Stapel gefunden wird, wird der **Pop** ignoriert.

Die- `#pragma pack (pop, r1, 2)` Anweisung entspricht, `#pragma pack (pop, r1)` gefolgt von `#pragma pack(2)`.

*Figur*\
Optionale Bei Verwendung mit **Push**weist dem Datensatz im internen compilerstapel einen Namen zu. Bei Verwendung mit **Pop**werden Datensätze vom internen Stapel bis zum Entfernen des *Bezeichners* angezeigt. Wenn der *Bezeichner* im internen Stapel nicht gefunden wird, wird nichts weitergeleitet.

*Nr*\
Optionale Gibt den Wert in Bytes an, der für das Packen verwendet werden soll. Wenn die Compileroption [/ZP](../build/reference/zp-struct-member-alignment.md) nicht für das Modul festgelegt ist, ist der Standardwert für *n* 8. Gültige Werte sind 1, 2, 4, 8 und 16. Die Ausrichtung eines Members erfolgt an einer Grenze, die entweder ein Vielfaches von *n*oder ein Vielfaches der Größe des Members ist, je nachdem, welcher Wert kleiner ist.

## <a name="remarks"></a>Bemerkungen

Um eine Klasse zu *Verpacken* , müssen Sie die zugehörigen Member direkt im Arbeitsspeicher platzieren. Dies kann bedeuten, dass einige oder alle Elemente an einer Grenze ausgerichtet werden können, die kleiner als die Standardausrichtung der Zielarchitektur ist. **Pack** übergibt die Steuerung auf der Ebene der Daten Deklaration. Dies unterscheidet sich von der Compileroption [/ZP](../build/reference/zp-struct-member-alignment.md), die nur Steuerelemente auf Modulebene bereitstellt. Das **Paket** tritt in **Kraft, nachdem**das Pragma **angezeigt wird.** **class** **Pack** hat keine Auswirkung auf Definitionen. Durch das Aufrufen von **Pack** ohne Argumente wird *n* auf den in der Compileroption `/Zp`festgelegten Wert festgelegt. Wenn die-Compileroption nicht festgelegt ist, ist der Standardwert 8 für x86, Arm und ARM64. Der Standardwert ist 16 für x64 Native.

Wenn Sie die Ausrichtung einer Struktur ändern, belegt sie vielleicht nicht so viel Platz im Arbeitsspeicher, aber Sie werden eine Abnahme der Leistung feststellen oder sogar eine von der Hardware generierte Ausnahme für einen nicht ausgerichteten Zugriff erhalten.  Sie können dieses Ausnahme Verhalten ändern, indem Sie "* [" verwenden.](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode)

Weitere Informationen zum Ändern der Ausrichtung finden Sie in den folgenden Artikeln:

- [__alignof](../cpp/alignof-operator.md)

- [abzustimmen](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [Beispiele für die Struktur Ausrichtung](../build/x64-software-conventions.md#examples-of-structure-alignment) (x64-spezifisch)

   > [!WARNING]
   > In Visual Studio 2015 und höher können Sie die Standard Operatoren " **alignas** " und " **alignof** " verwenden, die im Unterschied zu `__alignof` und `declspec( align )` über Compiler hinweg portabel sind. Wenn der C++-Standard keine Komprimierung adressiert, müssen Sie immer noch " **Pack** " (oder die entsprechende Erweiterung auf anderen Compilern) verwenden, um die Ausrichtungen anzugeben, die kleiner als die Wort Größe der Zielarchitektur sind.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird gezeigt, wie das **Pack** -Pragma verwendet wird, um die Ausrichtung einer Struktur zu ändern.

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

## <a name="see-also"></a>Weitere Informationen:

[Pragma-Direktiven und das __Pragma-Schlüsselwort](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
