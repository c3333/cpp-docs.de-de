---
title: CMFCAcceleratorKeyAssignCtrl-Klasse
ms.date: 10/18/2018
f1_keywords:
- CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::GetAccel
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsFocused
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::ResetKey
helpviewer_keywords:
- CMFCAcceleratorKeyAssignCtrl [MFC], CMFCAcceleratorKeyAssignCtrl
- CMFCAcceleratorKeyAssignCtrl [MFC], GetAccel
- CMFCAcceleratorKeyAssignCtrl [MFC], IsFocused
- CMFCAcceleratorKeyAssignCtrl [MFC], IsKeyDefined
- CMFCAcceleratorKeyAssignCtrl [MFC], PreTranslateMessage
- CMFCAcceleratorKeyAssignCtrl [MFC], ResetKey
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
ms.openlocfilehash: c7b60d9e695351e0c1d97b6629ff19664fcd6d05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369940"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>CMFCAcceleratorKeyAssignCtrl-Klasse

Die `CMFCAcceleratorKeyAssignCtrl` Klasse erweitert die [CEdit-Klasse,](../../mfc/reference/cedit-class.md) um zusätzliche Systemschaltflächen wie ALT, CONTROL und SHIFT zu unterstützen.

## <a name="syntax"></a>Syntax

```
class CMFCAcceleratorKeyAssignCtrl : public CEdit
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|Erstellt ein `CMFCAcceleratorKeyAssignCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|Ruft die `ACCEL`-Struktur für eine im `CMFCAcceleratorKeyAssignCtrl`-Objekt gedrückte Tastenkombination ab.|
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|Bestimmt, ob eine Tastenkombination definiert wurde.|
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|Wird von der Klasse [CWinApp](../../mfc/reference/cwinapp-class.md) verwendet, um Fensternachrichten zu übersetzen, bevor sie an die [TranslateMessage-](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage-Windows-Funktionen](/windows/win32/api/winuser/nf-winuser-dispatchmessage) gesendet werden. (Überschreibt [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|Setzt die Tastenkombination zurück.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse erweitert die Funktionalität der `CEdit`-Klasse, indem Sie Unterstützung von Tastenkombinationen hinzufügt, auch bekannt als Zugriffstasten. Die `CMFCAcceleratorKeyAssignCtrl` Klasse fungiert als [CEdit-Klasse](../../mfc/reference/cedit-class.md) und kann auch Systemschaltflächen erkennen.

Diese Klasse ordnet Zeichenfolgenwerten physische Tastenkombinationen zu. Angenommen die Tastenkombination ALT+B ist der Zeichenfolge „Alt + B“ zugeordnet. Wenn der Benutzer diese Tastenkombination in einem `CMFCAcceleratorKeyAssignCtrl`-Objekt drückt, wird ihm „Alt+B“ angezeigt. Weitere Informationen zur Zuordnung zwischen Tastenkombinationen und einem Zeichenfolgenformat finden Sie unter [CMFCAcceleratorKey Class](../../mfc/reference/cmfcacceleratorkey-class.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht das Erstellen eines `CMFCAcceleratorKeyAssignCtrl`-Objekts und die Verwendung der `ResetKey`-Methode zum Zurücksetzen der Tastenkombination.

[!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CMFCAcceleratorKeyAssignCtrl`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxacceleratorkeyassignctrl.h

## <a name="cmfcacceleratorkeyassignctrlcmfcacceleratorkeyassignctrl"></a><a name="cmfcacceleratorkeyassignctrl"></a>CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl

Erstellt ein [CMFCAcceleratorKeyAssignCtrl-Objekt.](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)

```
CMFCAcceleratorKeyAssignCtrl();
```

## <a name="cmfcacceleratorkeyassignctrlgetaccel"></a><a name="getaccel"></a>CMFCAcceleratorKeyAssignCtrl::GetAccel

Ruft die `ACCEL` Struktur für eine im [CMFCAcceleratorKeyAssignCtrl-Objekt](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) gedrückte Tastenkombination ab.

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>Rückgabewert

Eine `ACCEL` Struktur, die die Tastenkombination beschreibt.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese `ACCEL` Funktion, um die Struktur für `CMFCAcceleratorKeyAssignCtrl` eine Tastenkombination abzurufen, die der Benutzer in ihr Objekt eingegeben hat.

## <a name="cmfcacceleratorkeyassignctrlisfocused"></a><a name="isfocused"></a>CMFCAcceleratorKeyAssignCtrl::IsFocused

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcacceleratorkeyassignctrliskeydefined"></a><a name="iskeydefined"></a>CMFCAcceleratorKeyAssignCtrl::IsKeyDefined

Bestimmt, ob im [CMFCAcceleratorKeyAssignCtrl-Objekt](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) eine Tastenkombination definiert wurde.

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Benutzer bereits eine gültige Tastenkombination gedrückt hat, die eine Tastenkombination definiert. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um zu bestimmen, `CMFCAcceleratorKeyAssignCtrl` ob der Benutzer eine gültige Tastenkombination in das Objekt eingegeben hat. Wenn eine Tastenkombination vorhanden ist, können Sie die [CMFCAcceleratorKeyAssignCtrl::GetAccel-Methode](#getaccel) verwenden, um die Struktur abzufragen, die `ACCEL` dieser Tastenkombination zugeordnet ist.

## <a name="cmfcacceleratorkeyassignctrlpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parameter

[in] *pMsg*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcacceleratorkeyassignctrlresetkey"></a><a name="resetkey"></a>CMFCAcceleratorKeyAssignCtrl::ResetKey

Setzt die Tastenkombination zurück.

```
void ResetKey();
```

### <a name="remarks"></a>Bemerkungen

Die Funktion löscht den Bearbeitungssteuerelementtext. Dazu gehören alle Tastenkombinationen, die der Benutzer gedrückt hat.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAcceleratorKey-Klasse](../../mfc/reference/cmfcacceleratorkey-class.md)
