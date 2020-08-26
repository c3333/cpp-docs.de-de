---
title: Cmfcdisablemenuanimation-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
ms.openlocfilehash: 97a93e000b3e12d8ec4824100059581216b1b8d9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840764"
---
# <a name="cmfcdisablemenuanimation-class"></a>Cmfcdisablemenuanimation-Klasse

Deaktiviert die Popup Menü Animation.

## <a name="syntax"></a>Syntax

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|-|-|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Erstellt ein `CMFCDisableMenuAnimation`-Objekt.|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|-|-|
|[Cmfcdisablemenuanimation:: Restore](#restore)|Stellt die vorherige Animation wieder her, die vom Framework verwendet wurde, um ein Popupmenü anzuzeigen.|

### <a name="data-members"></a>Datenelemente

|Name|Beschreibung|
|-|-|
|`CMFCDisableMenuAnimation::m_animType`|Speichert den vorherigen Popup-Menü Animationstyp.|

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Hilfsklasse, um die Popup Menü Animation temporär zu deaktivieren (z. b. bei der Verarbeitung von Maus-oder Tastaturbefehlen).

Ein- `CMFCDisableMenuAnimation` Objekt deaktiviert die Popup Menü Animation während ihrer Lebensdauer. Der-Konstruktor speichert den aktuellen Aufgabentyp des Popup Menüs im `m_animType` -Feld und legt den aktuellen Animationstyp auf fest `CMFCPopupMenu::NO_ANIMATION` . Der Dekonstruktor stellt den vorherigen Animationstyp wieder her.

Sie können ein- `CMFCDisableMenuAnimation` Objekt auf dem Stapel erstellen, um die Popup Menü Animation in einer einzelnen Funktion zu deaktivieren. Wenn Sie die Popup Menü Animation zwischen Funktionen deaktivieren möchten, erstellen Sie ein `CMFCDisableMenuAnimation` -Objekt auf dem Heap, und löschen Sie es, wenn Sie die Popup Menü Animation wiederherstellen möchten.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie der Stapel verwendet wird, um die Menü Animation vorübergehend zu deaktivieren.

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cmfcdisablemenuanimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxpopupmenu. h

## <a name="cmfcdisablemenuanimationrestore"></a><a name="restore"></a> Cmfcdisablemenuanimation:: Restore

Stellt die vorherige Animation wieder her, die vom Framework verwendet wurde, um ein Popupmenü anzuzeigen.

```cpp
void Restore ();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode wird vom deaktivierer aufgerufen `CMFCDisableMenuAnimation` , um die vorherige Animation wiederherzustellen, die vom Framework zum Anzeigen eines Popup Menüs verwendet wurde.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[Cmfcpopupmenu-Klasse](../../mfc/reference/cmfcpopupmenu-class.md)
