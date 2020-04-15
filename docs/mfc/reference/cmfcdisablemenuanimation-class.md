---
title: CMFCDisableMenuAnimation-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
ms.openlocfilehash: 990f41d2dfa6491d246797322ee275c9648d52a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367570"
---
# <a name="cmfcdisablemenuanimation-class"></a>CMFCDisableMenuAnimation-Klasse

Deaktiviert die Popup-Menüanimation.

## <a name="syntax"></a>Syntax

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|Name|BESCHREIBUNG|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Erstellt ein `CMFCDisableMenuAnimation`-Objekt.|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCDisableMenuAnimation::Wiederherstellen](#restore)|Stellt die vorherige Animation wieder her, die das Framework zum Anzeigen eines Popupmenüs verwendet hat.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|Name|BESCHREIBUNG|
|`CMFCDisableMenuAnimation::m_animType`|Speichert den vorherigen Popupmenü-Animationstyp.|

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Hilfsklasse, um die Popupmenüanimation vorübergehend zu deaktivieren (z. B. wenn Sie Maus- oder Tastaturbefehle verarbeiten).

Ein `CMFCDisableMenuAnimation` Objekt deaktiviert die Popupmenüanimation während seiner Lebensdauer. Der Konstruktor speichert den aktuellen Popupmenü-Animationstyp im `m_animType` Feld `CMFCPopupMenu::NO_ANIMATION`und legt den aktuellen Animationstyp auf fest. Der Destruktor stellt den vorherigen Animationstyp wieder her.

Sie können `CMFCDisableMenuAnimation` ein Objekt auf dem Stapel erstellen, um die Popupmenüanimation in einer einzelnen Funktion zu deaktivieren. Wenn Sie die Popupmenüanimation zwischen Funktionen `CMFCDisableMenuAnimation` deaktivieren möchten, erstellen Sie ein Objekt auf dem Heap, und löschen Sie es dann, wenn Sie die Popupmenüanimation wiederherstellen möchten.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Sie den Stack verwenden, um die Menüanimation vorübergehend zu deaktivieren.

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxpopupmenu.h

## <a name="cmfcdisablemenuanimationrestore"></a><a name="restore"></a>CMFCDisableMenuAnimation::Wiederherstellen

Stellt die vorherige Animation wieder her, die das Framework zum Anzeigen eines Popupmenüs verwendet hat.

```
void Restore ();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode wird `CMFCDisableMenuAnimation` vom Destruktor aufgerufen, um die vorherige Animation wiederherzustellen, die das Framework zum Anzeigen eines Popupmenüs verwendet hat.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu-Klasse](../../mfc/reference/cmfcpopupmenu-class.md)
