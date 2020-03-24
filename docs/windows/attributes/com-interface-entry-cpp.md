---
title: COM_INTERFACE_ENTRY (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.com_interface_entry
helpviewer_keywords:
- com_interface_entry attribute
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
ms.openlocfilehash: d7b378baedd3f8c2720c7ab17698e8b416304061
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168303"
---
# <a name="com_interface_entry-c"></a>com_interface_entry (C++)

Fügt der com-Zuordnung der Zielklasse einen Schnittstellen Eintrag hinzu.

## <a name="syntax"></a>Syntax

```cpp
[ com_interface_entry(
  com_interface_entry) ]
```

### <a name="parameters"></a>Parameter

*com_interface_entry*<br/>
Eine Zeichenfolge, die den eigentlichen Text des Eintrags enthält. Eine Liste möglicher Werte finden Sie unter [COM_INTERFACE_ENTRY Makros](../../atl/reference/com-interface-entry-macros.md).

## <a name="remarks"></a>Bemerkungen

Das **COM_INTERFACE_ENTRY** C++ -Attribut fügt den ungekürzte Inhalt einer Zeichenfolge in die COM-Schnittstellen Zuordnung des Zielobjekts ein. Wenn das Attribut einmal auf das Zielobjekt angewendet wird, wird der Eintrag am Anfang der vorhandenen Schnittstellen Zuordnung eingefügt. Wenn das Attribut wiederholt auf dasselbe Zielobjekt angewendet wird, werden die Einträge am Anfang der Schnittstellen Zuordnung in der Reihenfolge eingefügt, in der Sie empfangen werden.

Dieses Attribut erfordert, dass die Attribute [coclass](coclass.md), [progid](progid.md), oder [vi_progid](vi-progid.md) (oder ein anderes Attribut, das eines der genannten impliziert) auch auf demselben Element angewendet werden. Wenn ein einzelnes Attribut verwendet wird, werden die anderen beiden automatisch angewendet. Wenn `progid` z. b. angewendet wird, werden `vi_progid` und `coclass` ebenfalls angewendet.

Da die erste Verwendung von **COM_INTERFACE_ENTRY** bewirkt, dass die neue Schnittstelle am Anfang der Schnittstellen Zuordnung eingefügt wird, muss es sich um einen der folgenden COM_INTERFACE_ENTRY Typen handeln:

- COM_INTERFACE_ENTRY

- COM_INTERFACE_ENTRY_IID

- COM_INTERFACE_ENTRY2

- COM_INTERFACE_ENTRY2_IID

Bei zusätzlichen Verwendungsmöglichkeiten des **COM_INTERFACE_ENTRY** -Attributs können alle unterstützten COM_INTERFACE_ENTRY Typen verwendet werden.

Diese Einschränkung ist erforderlich, da ATL den ersten Eintrag in der Schnittstellen Zuordnung als Identitäts `IUnknown`verwendet. Daher muss der Eintrag eine gültige Schnittstelle sein. Beispielsweise ist das folgende Codebeispiel ungültig, da der erste Eintrag in der Schnittstellen Zuordnung keine tatsächliche com-Schnittstelle angibt.

```cpp
[ coclass, com_interface_entry =
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"
]
   class CMyClass
   {
   };
```

## <a name="example"></a>Beispiel

Der folgende Code fügt der vorhandenen COM-Schnittstellen Zuordnung `CMyBaseClass`zwei Einträge hinzu. Der erste ist eine Standardschnittstelle, und der zweite blendet die `IDebugTest`-Schnittstelle aus.

```cpp
// cpp_attr_ref_com_interface_entry.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name ="ldld")];

[ object,
  uuid("7dbebed3-d636-4917-af62-c767a720a5b9")]
__interface IDebugTest{};

[ object,
  uuid("2875ceac-f94b-4087-8e13-d13dc167fcfc")]
__interface IMyClass{};

[ coclass,
  com_interface_entry ("COM_INTERFACE_ENTRY (IMyClass)"),
  com_interface_entry ("COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"),
  uuid("b85f8626-e76e-4775-b6a0-4826a9e94af2")
]

class CMyClass: public IMyClass, public IDebugTest
{
};
```

Die resultierende com-Objekt Zuordnung für `CMyBaseClass` lautet wie folgt:

```cpp
BEGIN_COM_MAP(CMyClass)
    COM_INTERFACE_ENTRY (IMyClass)
    COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)
    COM_INTERFACE_ENTRY(IMyClass)
    COM_INTERFACE_ENTRY2(IDispatch, IMyClass)
    COM_INTERFACE_ENTRY(IDebugTest)
    COM_INTERFACE_ENTRY(IProvideClassInfo)
END_COM_MAP()
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|**Klasse**, **Struktur**|
|**Wiederholbar**|Ja|
|**Erforderliche Attribute**|Eine oder mehrere der folgenden: `coclass`, `progid`oder `vi_progid`.|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[COM-Attribute](com-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[typedef-, enum-, union- und struct-Attribute](typedef-enum-union-and-struct-attributes.md)
