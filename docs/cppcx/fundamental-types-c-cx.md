---
title: Grundlegende Typen (C++/CX)
ms.date: 01/22/2017
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
ms.openlocfilehash: 3d484d9490a0a5b2ee2e7f92381528124b47701c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230999"
---
# <a name="fundamental-types-ccx"></a>Grundlegende Typen (C++/CX)

Zusätzlich zu den integrierten C++-Standardtypen unterstützt C++/CX das Typsystem, das durch die Windows-Runtime Architektur definiert ist, indem Typedefs für die Windows-Runtime grundlegenden Typen bereitgestellt werden, die Standard-C++-Typen zugeordnet sind. C++/CX implementiert grundlegende Typen von booleschen Werten, Zeichen und numerischen Werten. Dieser Typdefinitionen werden im `default` -Namespace definiert, der nicht explizit angegeben werden muss. Außerdem bietet C++/CX Wrapper und konkrete Implementierungen für bestimmte Windows-Runtime Typen und Schnittstellen.

## <a name="boolean-and-character-types"></a>Boolesche und Zeichentypen

Die folgende Tabelle enthält die integrierten booleschen und Zeichentypen sowie deren C++-Standardentsprechungen.

|Namespace|C++/CX Name|Definition|C++-Standardname|Wertebereich|
|---------------|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|Plattform|Boolesch|Ein 8-Bit-boolescher Wert.|bool|**`true`**(ungleich null) und **`false`** (null)|
|default|char16|Ein nicht numerischer 16-Bit-Wert, der einen Unicode-Codepunkt (UTF-16) darstellt.|wchar_t<br /><br /> Oder<br /><br /> L'c'|(Angegeben durch den Unicode-Standard)|

## <a name="numeric-types"></a>Numerische Typen

In der folgenden Tabelle sind die integrierten numerischen Typen aufgeführt. Die numerischen Typen sind im `default` -Namespace deklariert und stellen Typdefinitionen für den entsprechenden integrierten C++-Typ dar. Nicht alle integrierten C++-Typen (z. b. Long) werden in der Windows-Runtime unterstützt. Aus Gründen der Konsistenz und Übersichtlichkeit wird empfohlen, dass Sie den Namen C++/CX verwenden.

|C++/CX Name|Definition|C++-Standardname|Wertebereich|
|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|int8|Eine numerischer 8-Bit-Wert mit Vorzeichen.|char mit Vorzeichen|-128 bis 127|
|uint8|Eine numerischer 8-Bit-Wert ohne Vorzeichen.|unsigned char|0 bis 255|
|int16|Eine 16-Bit-Ganzzahl mit Vorzeichen.|short|-32.768 bis 32.767|
|uint16|Eine 16-Bit-Ganzzahl ohne Vorzeichen.|unsigned short|0 bis 65.535|
|int32|Eine 32-Bit-Ganzzahl mit Vorzeichen.|INT|-2.147.483.648 bis 2.147.483.647|
|uint32|Eine 32-Bit-Ganzzahl ohne Vorzeichen.|unsigned int|0 bis 4.294.967.295|
|int64|Eine 64-Bit-Ganzzahl mit Vorzeichen.|Long Long-oder-__int64|-9.223.372.036.854, 775.808 bis 9.223.372.036.854.775.807|
|uint64|Eine 64-Bit-Ganzzahl ohne Vorzeichen.|Ganzzahl ohne Vorzeichen long long-oder-Ganzzahl ohne Vorzeichen-__int64|0 bis 18.446.744.073.709.551.615|
|float32|Eine 32-Bit-IEEE 754-Gleitkommazahl.|float|3.4E +/- 38 (7 Stellen)|
|float64|Eine 64-Bit-IEEE 754-Gleitkommazahl.|double|1.7E +/- 308 (15 Stellen)|

## <a name="windows-runtime-types"></a>Windows-Runtime Typen

In der folgenden Tabelle sind einige zusätzliche Typen aufgeführt, die von der Windows-Runtime-Architektur definiert und in C++ integriert sind/CX. „Object“ und „String“ sind Referenztypen. Die anderen sind Werttypen. Alle diese Typen werden im `Platform` -Namespace deklariert. Eine vollständige Liste finden Sie unter [Platform namespace](../cppcx/platform-namespace-c-cx.md).

|Name|Definition|
|----------|----------------|
|Object|Stellt einen beliebigen Windows-Runtime Typ dar.|
|Zeichenfolge|Eine Reihe von Zeichen, die Text darstellen.|
|Rect|Eine Gruppe von vier Gleitkommazahlen, die die Position und Größe eines Rechtecks angeben.|
|SizeT|Ein geordnetes Paar von Gleitkommazahlen, die eine Höhe und Breite angeben.|
|Point|Ein geordnetes Paar von Gleitkommazahlen für x- und y-Koordinaten, die einen Punkt in einer zweidimensionalen Ebene definieren.|
|Guid|Ein nicht numerischer 128-Bit-Wert, der als eindeutiger Bezeichner verwendet wird.|
|UIntPtr|(Nur zur internen Verwendung.) Ein 64-Bit-Wert ohne Vorzeichen, der als Zeiger verwendet wird.|
|IntPtr|(Nur zur internen Verwendung.)  Ein 64-Bit-Wert mit Vorzeichen, der als Zeiger verwendet wird.|

## <a name="see-also"></a>Siehe auch

[Typensystem](../cppcx/type-system-c-cx.md)
