---
title: CPtrList-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPtrList
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
ms.openlocfilehash: d7da4fe52d25d9ffdf6371aa40f41d7082f1165c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226840"
---
# <a name="cptrlist-class"></a>CPtrList-Klasse

Unterstützt Listen void-Zeigern.

## <a name="syntax"></a>Syntax

```
class CPtrList : public CObject
```

## <a name="members"></a>Member

Die Member-Funktionen von `CPtrList` ähneln den Element Funktionen der-Klasse [CObList](../../mfc/reference/coblist-class.md). Aufgrund dieser Ähnlichkeit können Sie die `CObList`-Referenzdokumentation für Memberfunktionsbesonderheiten verwenden. `CObject`Wenn ein Zeiger als Funktionsparameter oder Rückgabewert angezeigt wird, ersetzen Sie einen Zeiger auf **`void`** .

`CObject*& CObList::GetHead() const;`

Beispielsweise übersetzt zu

`void*& CPtrList::GetHead() const;`

## <a name="remarks"></a>Bemerkungen

`CPtrList`integriert das IMPLEMENT_DYNAMIC Makro, um den Lauf Zeittyp Zugriff zu unterstützen und auf ein-Objekt zu sichern `CDumpContext` . Wenn Sie eine Sicherung einzelner Zeigerlistenelemente benötigen, müssen Sie die Tiefe des Sicherungskontexts auf 1 oder größer festlegen.

Zeigerlisten können nicht serialisiert werden.

Wenn ein `CPtrList`-Objekt gelöscht wird oder dessen Elemente entfernt werden, werden nur die Zeiger, und nicht die Entitäten, auf die sie verweisen, entfernt.

Weitere Informationen zur Verwendung von `CPtrList` finden Sie im Artikel [Sammlungen](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CPtrList`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcoll. h

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CObList-Klasse](../../mfc/reference/coblist-class.md)
