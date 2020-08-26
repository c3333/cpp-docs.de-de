---
title: importlib (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importlib
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
ms.openlocfilehash: 004533282ca089a076df6b110d52701abc16f71d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842220"
---
# <a name="importlib"></a>importlib

Stellt Typen, die bereits in einer anderen Typbibliothek kompiliert wurden, der erstellten Typbibliothek zur Verfügung.

## <a name="syntax"></a>Syntax

```cpp
[ importlib("tlb_file") ];
```

### <a name="parameters"></a>Parameter

*tlb_file*<br/>
Der Name einer TLB-Datei in Anführungszeichen, die in die Typbibliothek des aktuellen Projekts importiert werden soll.

## <a name="remarks"></a>Bemerkungen

Das **importlib** C++-Attribut bewirkt `importlib` , dass eine-Anweisung in den Bibliotheks Block der generierten IDL-Datei eingefügt wird. Das **importlib** -Attribut verfügt über die gleiche Funktionalität wie das [importlib](/windows/win32/Midl/importlib) -Attribut "Mittel l".

## <a name="example"></a>Beispiel

Der folgende Code zeigt ein Beispiel für die Verwendung von **importlib**:

```cpp
// cpp_attr_ref_importlib.cpp
// compile with: /LD
[module(name="MyLib")];
[importlib("importlib.tlb")];
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Überall|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[Compilerattribute](compiler-attributes.md)<br/>
[Eigenständige Attribute](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[darunter](include-cpp.md)<br/>
[Includelib](includelib-cpp.md)
