---
title: Cdwordarray-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDWordArray
- AFXCOLL/CDWordArray
- AFXCOLL/CDWordArray::CDWordArray
- AFXCOLL/CDWordArray::Add
- AFXCOLL/CDWordArray::Append
- AFXCOLL/CDWordArray::Copy
- AFXCOLL/CDWordArray::ElementAt
- AFXCOLL/CDWordArray::FreeExtra
- AFXCOLL/CDWordArray::GetAt
- AFXCOLL/CDWordArray::GetCount
- AFXCOLL/CDWordArray::GetData
- AFXCOLL/CDWordArray::GetSize
- AFXCOLL/CDWordArray::GetUpperBound
- AFXCOLL/CDWordArray::InsertAt
- AFXCOLL/CDWordArray::IsEmpty
- AFXCOLL/CDWordArray::RemoveAll
- AFXCOLL/CDWordArray::RemoveAt
- AFXCOLL/CDWordArray::SetAt
- AFXCOLL/CDWordArray::SetAtGrow
- AFXCOLL/CDWordArray::SetSize
helpviewer_keywords:
- CDWordArray [MFC], CDWordArray
- CDWordArray [MFC], Add
- CDWordArray [MFC], Append
- CDWordArray [MFC], Copy
- CDWordArray [MFC], ElementAt
- CDWordArray [MFC], FreeExtra
- CDWordArray [MFC], GetAt
- CDWordArray [MFC], GetCount
- CDWordArray [MFC], GetData
- CDWordArray [MFC], GetSize
- CDWordArray [MFC], GetUpperBound
- CDWordArray [MFC], InsertAt
- CDWordArray [MFC], IsEmpty
- CDWordArray [MFC], RemoveAll
- CDWordArray [MFC], RemoveAt
- CDWordArray [MFC], SetAt
- CDWordArray [MFC], SetAtGrow
- CDWordArray [MFC], SetSize
ms.assetid: 581be11e-ced6-47d1-8679-e0b8e7d99494
ms.openlocfilehash: f17caafd01bb5ddfa49afe378bfd79652149ebd8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447347"
---
# <a name="cdwordarray-class"></a>Cdwordarray-Klasse

Unterstützt 32-Bit-Doppelwortarrays.

## <a name="syntax"></a>Syntax

```
class CDWordArray : public CObject
```

## <a name="members"></a>Members

Die Member-Funktionen von `CDWordArray` ähneln den Element Funktionen der-Klasse [kobarray](../../mfc/reference/cobarray-class.md). Aufgrund dieser Ähnlichkeit können Sie die `CObArray`-Referenzdokumentation für Memberfunktionsbesonderheiten verwenden. Wenn ein `CObject` Zeiger als Funktionsparameter oder Rückgabewert angezeigt wird, ersetzen Sie einen `DWORD`.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

Beispielsweise übersetzt zu

`DWORD CDWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cdwordarray:: cdwordarray](../../mfc/reference/cobarray-class.md#cobarray)|Erstellt ein leeres Array.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cdwordarray:: Add](../../mfc/reference/cobarray-class.md#add)|Fügt am Ende des Arrays ein Element hinzu; vergrößert das Array bei Bedarf.|
|[Cdwordarray:: Append](../../mfc/reference/cobarray-class.md#append)|Hängt ein anderes Array an das Array an; vergrößert das Array bei Bedarf.|
|[Cdwordarray:: Copy](../../mfc/reference/cobarray-class.md#copy)|Kopiert ein anderes Array in das Array; vergrößert das Array bei Bedarf.|
|[Cdwordarray:: ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Gibt einen temporären Verweis auf das Byte im Array zurück.|
|[Cdwordarray:: freextra](../../mfc/reference/cobarray-class.md#freeextra)|Gibt den gesamten nicht verwendeten Arbeitsspeicher über der aktuellen Obergrenze frei.|
|[Cdwordarray:: GetAt](../../mfc/reference/cobarray-class.md#getat)|Gibt den Wert an einem bestimmten Index zurück.|
|[Cdwordarray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Ruft die Anzahl der Elemente im Array ab.|
|[Cdwordarray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|Ermöglicht den Zugriff auf Elemente im Array. Kann den Wert NULL haben.|
|[Cdwordarray:: GetSize](../../mfc/reference/cobarray-class.md#getsize)|Ruft die Anzahl der Elemente im Array ab.|
|[Cdwordarray:: GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Gibt den größten gültigen Index zurück.|
|[Cdwordarray:: InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Fügt ein Element (oder alle Elemente in einem anderen Array) am angegebenen Index ein.|
|[Cdwordarray:: IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Bestimmt, ob das Array leer ist.|
|[Cdwordarray:: RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Entfernt alle Elemente aus diesem Array.|
|[Cdwordarray:: RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Entfernt ein Element an einem spezifischen Index.|
|[Cdwordarray::](../../mfc/reference/cobarray-class.md#setat)|Legt den Wert für einen bestimmten Index fest; Array darf nicht vergrößert werden.|
|[Cdwordarray:: antatgrow](../../mfc/reference/cobarray-class.md#setatgrow)|Legt den Wert für einen bestimmten Index fest; vergrößert das Array bei Bedarf.|
|[Cdwordarray:: SetSize](../../mfc/reference/cobarray-class.md#setsize)|Legt die Anzahl der Elemente im Array fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cdwordarray:: Operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|Legt das Element am angegebenen Index fest oder ruft es ab.|

## <a name="remarks"></a>Bemerkungen

`CDWordArray` enthält das `IMPLEMENT_SERIAL`-Makro, um die Serialisierung und das Absichern der zugehörigen Elemente zu unterstützen. Wenn ein Array von Double words in einem Archiv gespeichert wird, entweder mit dem überladenen Einfügungs Operator ( **<<** ) oder mit der `Serialize` Member-Funktion, wird jedes Element wiederum serialisiert.

> [!NOTE]
>  Vor dem Verwenden eines Arrays, verwenden Sie `SetSize`, um dessen Größe festzustellen, und weisen dafür Arbeitsspeicher zu. Wenn Sie `SetSize` nicht verwenden, kann das Hinzufügen von Elementen zu Ihrem Array dazu führen, dass es häufig neu zugeordnet und kopiert wird. Häufige Neuzuordnungen und Kopiervorgänge sind ineffizient und können zu einer Fragmentierung des Arbeitsspeichers führen.

Wenn Sie die Debugausgabe einzelner Elemente im Array benötigen, müssen Sie die Tiefe des `CDumpContext` Objekts auf 1 oder höher festlegen.

Weitere Informationen zur Verwendung von `CDWordArray`finden Sie im Artikel [Sammlungen](../../mfc/collections.md).

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcoll. h

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CObArray-Klasse](../../mfc/reference/cobarray-class.md)
