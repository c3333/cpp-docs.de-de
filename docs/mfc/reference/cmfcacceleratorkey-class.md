---
title: CMFCAcceleratorKey-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
ms.openlocfilehash: a814618d3bda27d5b4ace12209dd93343ef2eef9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751778"
---
# <a name="cmfcacceleratorkey-class"></a>CMFCAcceleratorKey-Klasse

Eine Hilfsklasse, die die Zuordnung und Formatierung virtueller Schlüssel implementiert.

## <a name="syntax"></a>Syntax

```
class CMFCAcceleratorKey : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|Erstellt ein `CMFCAcceleratorKey`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCAcceleratorKey::Format](#format)|Übersetzt die ACCEL-Struktur in ihre visuelle Darstellung.|
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|Legt die Tastenkombination `CMFCAcceleratorKey` für das Objekt fest.|

## <a name="remarks"></a>Bemerkungen

Beschleunigerschlüssel werden auch als Tastenkombinationen bezeichnet. Wenn Sie Tastenkombinationen anzeigen möchten, die ein Benutzer eingibt, ordnet die [CMFCAcceleratorKeyAssignCtrl-Klasse](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) Tastenkombinationen, z. B. Alt+Umschalt+S, einem benutzerdefinierten Textformat wie "Alt + Shift + S" zu. Jedes `CMFCAcceleratorKey` Objekt ordnet einem Textformat eine einzelne Tastenkombination zu.

Weitere Informationen zur Verwendung von Tastenkombinationen und Beschleunigertabellen finden Sie unter [CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird `CMFCAcceleratorKey` veranschaulicht, wie ein `Format` Objekt erstellt und wie seine Methode verwendet wird.

[!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CMFCAcceleratorKey`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxacceleratorkey.h

## <a name="cmfcacceleratorkeycmfcacceleratorkey"></a><a name="cmfcacceleratorkey"></a>CMFCAcceleratorKey::CMFCAcceleratorKey

Erstellt ein [CMFCAcceleratorKey-Objekt.](../../mfc/reference/cmfcacceleratorkey-class.md)

```
CMFCAcceleratorKey();
CMFCAcceleratorKey(LPACCEL lpAccel);
```

### <a name="parameters"></a>Parameter

*lpAccel*<br/>
[in] Ein Zeiger auf eine Tastenkombination.

### <a name="remarks"></a>Bemerkungen

Wenn Sie beim Erstellen einer `CMFCAccleratorKey`keine Tastenkombination angeben, verwenden Sie die [CMFCAcceleratorKey::SetAccelerator-Methode,](#setaccelerator) um Ihrem `CMFCAcceleratorKey` Objekt eine Tastenkombination zuzuordnen.

## <a name="cmfcacceleratorkeyformat"></a><a name="format"></a>CMFCAcceleratorKey::Format

Übersetzt die ACCEL-Struktur in den zugeordneten Zeichenfolgenwert.

```cpp
void Format(CString& str) const;
```

### <a name="parameters"></a>Parameter

*Str*<br/>
[out] Ein Verweis `CString` auf ein Objekt, bei dem die Methode die übersetzte Tastenkombination schreibt.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft das Zeichenfolgenformat der zugeordneten Tastenkombination ab. Sie können das Zeichenfolgenformat eines [CMFCAcceleratorKey-Objekts](../../mfc/reference/cmfcacceleratorkey-class.md) entweder mit dem Konstruktor oder der Methode [CMFCAcceleratorKey::SetAccelerator](#setaccelerator)festlegen.

## <a name="cmfcacceleratorkeysetaccelerator"></a><a name="setaccelerator"></a>CMFCAcceleratorKey::SetAccelerator

Legt die Tastenkombination für das [CMFCAcceleratorKey-Objekt](../../mfc/reference/cmfcacceleratorkey-class.md) fest.

```cpp
void SetAccelerator(LPACCEL lpAccel);
```

### <a name="parameters"></a>Parameter

*lpAccel*<br/>
[in] Ein Zeiger auf eine Tastenkombination.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um `CMFCAcceleratorKey` die Tastenkombination für eine festzulegen, `CMFCAcceleratorKey`wenn Sie beim Erstellen der keine Tastenkombination zur Verfügung gestellt haben.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager-Klasse](../../mfc/reference/ckeyboardmanager-class.md)
