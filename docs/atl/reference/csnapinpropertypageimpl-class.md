---
title: CSnapInPropertyPageImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CancelToClose
- ATLSNAP/ATL::CSnapInPropertyPageImpl::Create
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnApply
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnHelp
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnKillActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnQueryCancel
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnReset
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnSetActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardBack
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardFinish
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardNext
- ATLSNAP/ATL::CSnapInPropertyPageImpl::QuerySiblings
- ATLSNAP/ATL::CSnapInPropertyPageImpl::SetModified
- ATLSNAP/ATL::CSnapInPropertyPageImpl::m_psp
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
ms.openlocfilehash: 3f09e8500eadd36eec53db95f10261834d672101
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747577"
---
# <a name="csnapinpropertypageimpl-class"></a>CSnapInPropertyPageImpl-Klasse

Diese Klasse stellt Methoden zum Implementieren eines Snap-In-Eigenschaftenseitenobjekts bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
CSnapInPropertyPageImpl : public CDialogImplBase
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSnapInPropertyPageImpl::AbbrechenToClose](#canceltoclose)|Ändert den Status der Schaltflächen **OK** und **Abbrechen.**|
|[CSnapInPropertyPageImpl::Erstellen](#create)|Initialisiert ein neu `CSnapInPropertyPageImpl` erstelltes Objekt.|
|[CSnapInPropertyPageImpl::OnApply](#onapply)|Wird vom Framework aufgerufen, wenn der Benutzer auf die Schaltfläche **Jetzt anwenden** klickt, während er ein Eigenschaftenblatt vom Assistenten verwendet.|
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|Wird vom Framework aufgerufen, wenn der Benutzer auf die **Schaltfläche Hilfe** klickt, während er ein Eigenschaftenblatt vom Assistenten-Typ verwendet.|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|Wird vom Framework aufgerufen, wenn die aktuelle Seite nicht mehr aktiv ist.|
|[CSnapInPropertyPageImpl::OnQuerycancel](#onquerycancel)|Wird vom Framework aufgerufen, wenn der Benutzer auf die Schaltfläche **Abbrechen** klickt und bevor der Abbruch erfolgt ist.|
|[CSnapInPropertyPageImpl::OnReset](#onreset)|Wird vom Framework aufgerufen, wenn der Benutzer auf die Schaltfläche **Zurücksetzen** klickt, während er ein Eigenschaftenblatt vom Assistenten verwendet.|
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|Wird vom Framework aufgerufen, wenn die aktuelle Seite aktiv wird.|
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|Wird vom Framework aufgerufen, wenn der Benutzer auf die Schaltfläche **Zurück** klickt, während er ein Eigenschaftenblatt vom Assistenten-Typ verwendet.|
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|Wird vom Framework aufgerufen, wenn der Benutzer auf die Schaltfläche **Fertig stellen** klickt, während er ein Eigenschaftenblatt vom Assistenten-Typ verwendet.|
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|Wird vom Framework aufgerufen, wenn der Benutzer auf die Schaltfläche **Weiter** klickt, während er ein Eigenschaftenblatt vom Assistenten-Typ verwendet.|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|Leitet die aktuelle Nachricht an alle Seiten des Eigenschaftenblatts weiter.|
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|Rufen Sie an, um die Schaltfläche **Jetzt anwenden** zu aktivieren oder zu deaktivieren.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Die `PROPSHEETPAGE` vom `CSnapInPropertyPageImpl` Objekt verwendete Windows-Struktur.|

## <a name="remarks"></a>Bemerkungen

`CSnapInPropertyPageImpl`stellt eine grundlegende Implementierung für ein Snap-In-Eigenschaftenseitenobjekt bereit. Die grundlegenden Features einer Snap-In-Eigenschaftsseite werden mithilfe verschiedener Schnittstellen und Kartentypen implementiert.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlsnap.h

## <a name="csnapinpropertypageimplcanceltoclose"></a><a name="canceltoclose"></a>CSnapInPropertyPageImpl::AbbrechenToClose

Rufen Sie diese Funktion auf, nachdem eine nicht wiederherstellbare Änderung an den Daten auf einer Seite eines modalen Eigenschaftenblatts vorgenommen wurde.

```cpp
void CancelToClose();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion ändert die **Schaltfläche OK** in **Schließen** und Deaktivieren der **Schaltfläche Abbrechen.** Diese Änderung warnt den Benutzer, dass eine Änderung dauerhaft ist und die Änderungen nicht abgebrochen werden können.

Die `CancelToClose` Memberfunktion führt in einem moduslosen Eigenschaftenblatt nichts aus, da ein modusloses Eigenschaftenblatt standardmäßig nicht über eine **Schaltfläche Abbrechen** verfügt.

## <a name="csnapinpropertypageimplcsnapinpropertypageimpl"></a><a name="csnapinpropertypageimpl"></a>CSnapInPropertyPageImpl::CSnapInPropertyPageImpl

Erstellt ein `CSnapInPropertyPageImpl`-Objekt.

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>Parameter

*lpszTitle*<br/>
[in] Der Titel der Eigenschaftenseite.

### <a name="remarks"></a>Bemerkungen

Um die zugrunde liegende Struktur zu initialisieren, rufen Sie [CSnapInPropertyPageImpl::Create](#create)auf.

## <a name="csnapinpropertypageimplcreate"></a><a name="create"></a>CSnapInPropertyPageImpl::Erstellen

Rufen Sie diese Funktion auf, um die zugrunde liegende Struktur der Eigenschaftenseite zu initialisieren.

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>Rückgabewert

Ein Handle `PROPSHEETPAGE` für eine Struktur, die die Attribute des neu erstellten Eigenschaftenblatts enthält.

### <a name="remarks"></a>Bemerkungen

Sie sollten zuerst [CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl) aufrufen, bevor Sie diese Funktion aufrufen.

## <a name="csnapinpropertypageimplm_psp"></a><a name="m_psp"></a>CSnapInPropertyPageImpl::m_psp

`m_psp`ist eine Struktur, deren `PROPSHEETPAGE`Member die Eigenschaften von speichern.

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Struktur, um die Darstellung einer Eigenschaftenseite nach dem Erstellen zu initialisieren.

Weitere Informationen zu dieser Struktur, einschließlich einer Liste ihrer Mitglieder, finden Sie unter [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v3) im Windows SDK.

## <a name="csnapinpropertypageimplonapply"></a><a name="onapply"></a>CSnapInPropertyPageImpl::OnApply

Diese Memberfunktion wird aufgerufen, wenn der Benutzer auf die Schaltfläche **OK** oder **Jetzt anwenden** klickt.

```
BOOL OnApply();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Änderungen akzeptiert werden; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Bevor `OnApply` sie vom Framework aufgerufen werden `SetModified` können, müssen Sie den Parameter true aufgerufen und festgelegt haben. Dadurch wird die Schaltfläche **Jetzt anwenden** aktiviert, sobald der Benutzer eine Änderung auf der Eigenschaftenseite vornimmt.

Überschreiben Sie diese Memberfunktion, um anzugeben, welche Aktion Ihr Programm ausführt, wenn der Benutzer auf die Schaltfläche **Jetzt anwenden** klickt. Beim Überschreiben sollte die Funktion TRUE zurückgeben, um Änderungen und FALSE zu akzeptieren, um zu verhindern, dass Änderungen wirksam werden.

Die Standardimplementierung `OnApply` von returns TRUE.

## <a name="csnapinpropertypageimplonhelp"></a><a name="onhelp"></a>CSnapInPropertyPageImpl::OnHelp

Diese Memberfunktion wird aufgerufen, wenn der Benutzer auf die **Schaltfläche Hilfe** für die Eigenschaftenseite klickt.

```cpp
void OnHelp();
```

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Memberfunktion, um Hilfe für die Eigenschaftenseite anzuzeigen.

## <a name="csnapinpropertypageimplonkillactive"></a><a name="onkillactive"></a>CSnapInPropertyPageImpl::OnKillActive

Diese Memberfunktion wird aufgerufen, wenn die Seite nicht mehr die aktive Seite ist.

```
BOOL OnKillActive();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn Daten erfolgreich aktualisiert wurden; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Memberfunktion, um spezielle Datenüberprüfungsaufgaben auszuführen.

## <a name="csnapinpropertypageimplonquerycancel"></a><a name="onquerycancel"></a>CSnapInPropertyPageImpl::OnQuerycancel

Diese Memberfunktion wird aufgerufen, wenn der Benutzer auf die Schaltfläche **Abbrechen** klickt und bevor die Abbruchaktion ausgeführt wurde.

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, um den Abbruchvorgang zuzulassen; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Memberfunktion, um eine Aktion anzugeben, die das Programm ausführt, wenn der Benutzer auf die Schaltfläche **Abbrechen** klickt.

Die Standardimplementierung `OnQueryCancel` von returns TRUE.

## <a name="csnapinpropertypageimplonreset"></a><a name="onreset"></a>CSnapInPropertyPageImpl::OnReset

Diese Memberfunktion wird aufgerufen, wenn der Benutzer auf die Schaltfläche **Abbrechen** klickt.

```cpp
void OnReset();
```

### <a name="remarks"></a>Bemerkungen

Wenn diese Funktion aufgerufen wird, werden Änderungen an allen Eigenschaftenseiten, die vom Benutzer vorgenommen wurden, der zuvor auf die Schaltfläche **Jetzt anwenden** geklickt hat, verworfen, und das Eigenschaftenblatt behält den Fokus bei.

Überschreiben Sie diese Memberfunktion, um anzugeben, welche Aktion das Programm ausführt, wenn der Benutzer auf die Schaltfläche **Abbrechen** klickt.

## <a name="csnapinpropertypageimplonsetactive"></a><a name="onsetactive"></a>CSnapInPropertyPageImpl::OnSetActive

Diese Memberfunktion wird aufgerufen, wenn die Seite vom Benutzer ausgewählt wird und zur aktiven Seite wird.

```
BOOL OnSetActive();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Seite erfolgreich aktiv festgelegt wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Memberfunktion, um Aufgaben auszuführen, wenn eine Seite aktiviert ist. Ihre Außerkraftsetzung dieser Memberfunktion sollte die Standardversion aufrufen, bevor eine andere Verarbeitung durchgeführt wird.

Die Standardimplementierung gibt TRUE zurück.

## <a name="csnapinpropertypageimplonwizardback"></a><a name="onwizardback"></a>CSnapInPropertyPageImpl::OnWizardBack

Diese Memberfunktion wird aufgerufen, wenn der Benutzer in einem Assistenten auf die Schaltfläche **"Zurück"** klickt.

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>Rückgabewert

- 0, um automatisch zur vorherigen Seite zu gelangen.

- -1, um zu verhindern, dass die Seite geändert wird.

Um zu einer anderen Seite als der nächsten zu springen, geben Sie den Bezeichner des anzuzeigenden Dialogfelds zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Memberfunktion, um eine Aktion anzugeben, die der Benutzer ausführen muss, wenn auf die **Schaltfläche "Zurück"** geklickt wird.

## <a name="csnapinpropertypageimplonwizardfinish"></a><a name="onwizardfinish"></a>CSnapInPropertyPageImpl::OnWizardFinish

Diese Memberfunktion wird aufgerufen, wenn der Benutzer in einem Assistenten auf die Schaltfläche **Fertig stellen** klickt.

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Eigenschaftenblatt zerstört wird, wenn der Assistent abgeschlossen ist. andernfalls Null.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Memberfunktion, um eine Aktion anzugeben, die der Benutzer ausführen muss, wenn auf die Schaltfläche **Fertig** stellen geklickt wird.

## <a name="csnapinpropertypageimplonwizardnext"></a><a name="onwizardnext"></a>CSnapInPropertyPageImpl::OnWizardNext

Diese Memberfunktion wird aufgerufen, wenn der Benutzer in einem Assistenten auf die Schaltfläche **Weiter** klickt.

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>Rückgabewert

- 0, um automatisch zur nächsten Seite zu gelangen.

- -1, um zu verhindern, dass die Seite geändert wird.

Um zu einer anderen Seite als der nächsten zu springen, geben Sie den Bezeichner des anzuzeigenden Dialogfelds zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Memberfunktion, um eine Aktion anzugeben, die der Benutzer ausführen muss, wenn auf die Schaltfläche **Weiter** geklickt wird.

## <a name="csnapinpropertypageimplquerysiblings"></a><a name="querysiblings"></a>CSnapInPropertyPageImpl::QuerySiblings

Rufen Sie diese Memberfunktion auf, um eine Nachricht an jede Seite im Eigenschaftenblatt weiterzuleiten.

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>Parameter

*wParam*<br/>
[in] Gibt zusätzliche nachrichtenabhängige Informationen an.

*lParam*<br/>
[in] Gibt zusätzliche nachrichtenabhängige Informationen an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Nachricht nicht an die nächste Eigenschaftenseite weitergeleitet werden soll. andernfalls Null.

### <a name="remarks"></a>Bemerkungen

Wenn eine Seite einen Wert ungleich Null zurückgibt, sendet das Eigenschaftenblatt die Nachricht nicht an nachfolgende Seiten.

## <a name="csnapinpropertypageimplsetmodified"></a><a name="setmodified"></a>CSnapInPropertyPageImpl::SetModified

Rufen Sie diese Memberfunktion auf, um die Schaltfläche **Jetzt anwenden** zu aktivieren oder zu deaktivieren, je nachdem, ob die Einstellungen auf der Eigenschaftenseite auf das entsprechende externe Objekt angewendet werden sollen.

```cpp
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parameter

*bChanged*<br/>
[in] TRUE, um anzugeben, dass die Eigenschaftenseiteneinstellungen seit der letzten Anwendung geändert wurden; FALSE, um anzugeben, dass die Eigenschaftenseiteneinstellungen angewendet wurden oder ignoriert werden sollten.

### <a name="remarks"></a>Bemerkungen

Das Eigenschaftenblatt verfolgt, welche Seiten "schmutzig" sind, d. h. Eigenschaftenseiten, für die Sie aufgerufen `SetModified( TRUE )`haben. Die Schaltfläche **Jetzt anwenden** wird immer `SetModified( TRUE )` aktiviert, wenn Sie eine der Seiten aufrufen. Die Schaltfläche **Jetzt anwenden** wird `SetModified( FALSE )` deaktiviert, wenn Sie eine der Seiten aufrufen, jedoch nur, wenn keine der anderen Seiten "schmutzig" ist.

## <a name="see-also"></a>Weitere Informationen

[Klassenübersicht](../../atl/atl-class-overview.md)
