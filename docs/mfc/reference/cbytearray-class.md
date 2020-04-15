---
title: CByteArray-Klasse
ms.date: 11/04/2016
f1_keywords:
- CByteArray
- AFXCOLL/CByteArray
- AFXCOLL/CByteArray::CByteArray
- AFXCOLL/CByteArray::Add
- AFXCOLL/CByteArray::Append
- AFXCOLL/CByteArray::Copy
- AFXCOLL/CByteArray::ElementAt
- AFXCOLL/CByteArray::FreeExtra
- AFXCOLL/CByteArray::GetAt
- AFXCOLL/CByteArray::GetCount
- AFXCOLL/CByteArray::GetData
- AFXCOLL/CByteArray::GetSize
- AFXCOLL/CByteArray::GetUpperBound
- AFXCOLL/CByteArray::InsertAt
- AFXCOLL/CByteArray::IsEmpty
- AFXCOLL/CByteArray::RemoveAll
- AFXCOLL/CByteArray::RemoveAt
- AFXCOLL/CByteArray::SetAt
- AFXCOLL/CByteArray::SetAtGrow
- AFXCOLL/CByteArray::SetSize
helpviewer_keywords:
- CByteArray [MFC], CByteArray
- CByteArray [MFC], Add
- CByteArray [MFC], Append
- CByteArray [MFC], Copy
- CByteArray [MFC], ElementAt
- CByteArray [MFC], FreeExtra
- CByteArray [MFC], GetAt
- CByteArray [MFC], GetCount
- CByteArray [MFC], GetData
- CByteArray [MFC], GetSize
- CByteArray [MFC], GetUpperBound
- CByteArray [MFC], InsertAt
- CByteArray [MFC], IsEmpty
- CByteArray [MFC], RemoveAll
- CByteArray [MFC], RemoveAt
- CByteArray [MFC], SetAt
- CByteArray [MFC], SetAtGrow
- CByteArray [MFC], SetSize
ms.assetid: 53d4a512-657c-4187-9609-e3f5339a78e0
ms.openlocfilehash: 9da30f6546a69a51c56bf4b27668e1603c13290b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352390"
---
# <a name="cbytearray-class"></a>CByteArray-Klasse

Unterstützt dynamische Bytearrays.

## <a name="syntax"></a>Syntax

```
class CByteArray : public CObject
```

## <a name="members"></a>Member

Die Memberfunktionen `CByteArray` von ähneln den Memberfunktionen der Klasse [CObArray](../../mfc/reference/cobarray-class.md). Aufgrund dieser Ähnlichkeit können Sie die `CObArray`-Referenzdokumentation für Memberfunktionsbesonderheiten verwenden. Ersetzen Sie `CObject` überall dort, wo Sie einen Zeiger als Funktionsparameter oder Rückgabewert sehen, ersetzen Sie ein BYTE.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

Beispielsweise übersetzt zu

`BYTE CByteArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CByteArray::CByteArray](../../mfc/reference/cobarray-class.md#cobarray)|Erstellt ein leeres Array.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CByteArray::Hinzufügen](../../mfc/reference/cobarray-class.md#add)|Fügt am Ende des Arrays ein Element hinzu; vergrößert das Array bei Bedarf.|
|[CByteArray::Anfügen](../../mfc/reference/cobarray-class.md#append)|Hängt ein anderes Array an das Array an; vergrößert das Array bei Bedarf.|
|[CByteArray::Kopieren](../../mfc/reference/cobarray-class.md#copy)|Kopiert ein anderes Array in das Array; vergrößert das Array bei Bedarf.|
|[CByteArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Gibt einen temporären Verweis auf das Byte innerhalb des Arrays zurück.|
|[CByteArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Gibt den gesamten nicht verwendeten Arbeitsspeicher über der aktuellen Obergrenze frei.|
|[CByteArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Gibt den Wert an einem bestimmten Index zurück.|
|[CByteArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Ruft die Anzahl der Elemente im Array ab.|
|[CByteArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Ermöglicht den Zugriff auf Elemente im Array. Kann den Wert NULL haben.|
|[CByteArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Ruft die Anzahl der Elemente im Array ab.|
|[CByteArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Gibt den größten gültigen Index zurück.|
|[CByteArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Fügt ein Element (oder alle Elemente in einem anderen Array) am angegebenen Index ein.|
|[CByteArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Bestimmt, ob das Array leer ist.|
|[CByteArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Entfernt alle Elemente aus diesem Array.|
|[CByteArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Entfernt ein Element an einem spezifischen Index.|
|[CByteArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Legt den Wert für einen bestimmten Index fest; Array darf nicht vergrößert werden.|
|[CByteArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Legt den Wert für einen bestimmten Index fest; vergrößert das Array bei Bedarf.|
|[CByteArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Legt die Anzahl der Elemente im Array fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CByteArray::Operator \[\]](../../mfc/reference/cobarray-class.md#operator_at)|Legt das Element am angegebenen Index fest oder ruft es ab.|

## <a name="remarks"></a>Bemerkungen

`CByteArray`enthält das IMPLEMENT_SERIAL Makro, um die Serialisierung und das Dumping seiner Elemente zu unterstützen. Wenn ein Array von Bytes in einem Archiv gespeichert **<<** wird, entweder `Serialize` mit dem Operator überladene einzufügen ( ) oder mit der Memberfunktion, wird jedes Element wiederum serialisiert.

> [!NOTE]
> Vor dem Verwenden eines Arrays, verwenden Sie `SetSize`, um dessen Größe festzustellen, und weisen dafür Arbeitsspeicher zu. Wenn Sie `SetSize` nicht verwenden, kann das Hinzufügen von Elementen zu Ihrem Array dazu führen, dass es häufig neu zugeordnet und kopiert wird. Häufige Neuzuordnungen und Kopiervorgänge sind ineffizient und können zu einer Fragmentierung des Arbeitsspeichers führen.

Wenn Sie die Debugausgabe einzelner Elemente im Array benötigen, `CDumpContext` müssen Sie die Tiefe des Objekts auf 1 oder höher festlegen.

Weitere Informationen zur `CByteArray`Verwendung finden Sie im Artikel [Sammlungen](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CByteArray`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxcoll.h

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CObArray-Klasse](../../mfc/reference/cobarray-class.md)
