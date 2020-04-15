---
title: CWinFormsControl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CWinFormsControl
- AFXWINFORMS/CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CreateManagedControl
- AFXWINFORMS/CWinFormsControl::GetControl
- AFXWINFORMS/CWinFormsControl::GetControlHandle
helpviewer_keywords:
- CWinFormsControl [MFC], CWinFormsControl
- CWinFormsControl [MFC], CreateManagedControl
- CWinFormsControl [MFC], GetControl
- CWinFormsControl [MFC], GetControlHandle
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
ms.openlocfilehash: c91f50be1ea30efac81ff67c43633bedd7b0ca03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377183"
---
# <a name="cwinformscontrol-class"></a>CWinFormsControl-Klasse

Stellt die grundlegende Funktionalität zum Hosten eines Windows Forms-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
template<class TManagedControl>
class CWinFormsControl : public CWnd
```

#### <a name="parameters"></a>Parameter

*TManagedControl*<br/>
Ein .NET Framework Windows Forms-Steuerelement, das in der MFC-Anwendung angezeigt werden soll.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|Erstellt ein MFC Windows Forms-Steuerelement-Wrapperobjekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|Erstellt ein Windows Forms-Steuerelement in einem MFC-Container.|
|[CWinFormsControl::GetControl](#getcontrol)|Ruft einen Zeiger auf das Windows Forms-Steuerelement ab.|
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|Ruft ein Handle für das Windows Forms-Steuerelement ab.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinFormsControl::operator -&gt;](#operator_-_gt)|Ersetzt [CWinFormsControl::GetControl](#getcontrol) in Ausdrücken.|
|[CWinFormsControl::operator TManagedControl](#operator_tmanagedcontrol)|Gibt einen Typ als Zeiger auf ein Windows Forms-Steuerelement um.|

## <a name="remarks"></a>Bemerkungen

Die `CWinFormsControl` Klasse stellt die grundlegende Funktionalität für das Hosten eines Windows Forms-Steuerelements bereit.

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden einer Windows Form Benutzersteuerung in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Ihr MFC-Code sollte Fensterhandles (normalerweise in `m_hWnd`gespeichert) nicht zwischenspeichern. Einige Windows Forms-Steuerelementeigenschaften erfordern, `Window` dass der zugrunde `DestroyWindow` liegende `CreateWindow`Win32 zerstört und mithilfe von und neu erstellt wird. Die MFC Windows Forms-Implementierung verarbeitet die `Destroy` und `Create` `m_hWnd` Ereignisse der Steuerelemente, um den Member zu aktualisieren.

> [!NOTE]
> Die MFC Windows Forms-Integration funktioniert nur in Projekten, die dynamisch mit MFC verknüpft sind (in denen AFXDLL definiert ist).

## <a name="requirements"></a>Anforderungen

**Kopf:** afxwinforms.h

## <a name="cwinformscontrolcreatemanagedcontrol"></a><a name="createmanagedcontrol"></a>CWinFormsControl::CreateManagedControl

Erstellt ein Windows Forms-Steuerelement in einem MFC-Container.

```
inline BOOL CreateManagedControl(
    System::Type^ pType,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID)
inline BOOL CreateManagedControl(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);

inline BOOL CreateManagedControl(
    DWORD dwStyle,
    int nPlaceHolderID,
    CWnd* pParentWnd);

inline BOOL CreateManagedControl(
    typename TManagedControl^ pControl,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);
```

### <a name="parameters"></a>Parameter

*pType*<br/>
Der Datentyp des zu erstellenden Steuerelements. Muss ein [Typdatentyp](/dotnet/api/system.type) sein.

*dwStyle*<br/>
Der Fensterstil, der auf das Steuerelement angewendet werden soll. Geben Sie eine Kombination aus [Fensterstilen an.](../../mfc/reference/styles-used-by-mfc.md#window-styles) Derzeit werden nur die folgenden Stile unterstützt: WS_TABSTOP, WS_VISIBLE, WS_DISABLED und WS_GROUP.

*Rect*<br/>
Eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Koordinaten der oberen linken und unteren rechten Ecken des Steuerelements definiert (nur die erste Überladung).

*nPlaceHolderID*<br/>
Der Griff des statischen Platzhaltersteuerelements, das im Ressourcen-Editor platziert wird. Das neu erstellte Windows Forms-Steuerelement ersetzt das statische Steuerelement unter der Annahme seiner Position, z-Reihenfolge und Stile (nur zweite Überladung).

*pParentWnd*<br/>
Ein Zeiger auf das übergeordnete Fenster.

*nID*<br/>
Die Ressourcen-ID-Nummer, die dem neu erstellten Steuerelement zugewiesen werden soll.

*pControl*<br/>
Eine Instanz eines Windows Forms-Steuerelements, das dem [CWinFormsControl-Objekt](../../mfc/reference/cwinformscontrol-class.md) zugeordnet werden soll (nur vierte Überladung).

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, gibt ein Wert ungleich Null zurück. Wenn dies nicht der Nachschlagen de/A/Liegt, wird Null zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Diese Methode instanziiert ein .NET Framework Windows Forms-Steuerelement in einem MFC-Container.

Die erste Überladung der Methode akzeptiert einen .NET Framework-Datentyp *pType,* sodass MFC ein neues Objekt dieses Typs instanziieren kann. *pType* muss ein [Typdatentyp](/dotnet/api/system.type) sein.

Die zweite Überladung der Methode erstellt ein `TManagedControl` Windows Forms-Steuerelement basierend auf dem Vorlagenparameter der `CWinFormsControl` Klasse. Die Größe und Position des Steuerelements basiert auf der Struktur, die `RECT` an die Methode übergeben wird. Nur *dwStyle* ist für die Stile wichtig.

Die dritte Überladung der Methode erstellt ein Windows Forms-Steuerelement, das ein statisches Steuerelement ersetzt, es zerstört und seine Position, Z-Reihenfolge und Stile annimmt. Das statische Steuerelement dient nur als Platzhalter für das Windows Forms-Steuerelement. Beim Erstellen des Steuerelements kombiniert diese Überladung die Stile von *dwStyle* mit den Ressourcenstilen des statischen Steuerelements.

Mit der vierten Überladung der Methode können Sie ein bereits instanziiertes Windows Forms-Steuerelement *pControl* übergeben, das Von MFC umschließt. Sie muss vom gleichen Typ `TManagedControl` wie der `CWinFormsControl` Vorlagenparameter der Klasse sein.

Weitere Informationen finden [Sie unter Verwenden einer Windows-Formularbenutzersteuerung in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) für Beispiele zur Verwendung von Windows Form-Steuerelementen.

## <a name="cwinformscontrolcwinformscontrol"></a><a name="cwinformscontrol"></a>CWinFormsControl::CWinFormsControl

Erstellt ein MFC Windows Forms-Steuerelement-Wrapperobjekt.

```
CWinFormsControl();
```

### <a name="remarks"></a>Bemerkungen

Das Windows Forms-Steuerelement wird instanziiert, wenn Sie [CWinFormsControl::CreateManagedControl](#createmanagedcontrol)aufrufen.

## <a name="cwinformscontrolgetcontrol"></a><a name="getcontrol"></a>CWinFormsControl::GetControl

Ruft einen Zeiger auf das Windows Forms-Steuerelement ab.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf das Windows Forms-Steuerelement zurück.

### <a name="example"></a>Beispiel

  Siehe [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).

## <a name="cwinformscontrolgetcontrolhandle"></a><a name="getcontrolhandle"></a>CWinFormsControl::GetControlHandle

Ruft ein Handle für das Windows Forms-Steuerelement ab.

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt ein Handle an das Windows Forms-Steuerelement zurück.

### <a name="remarks"></a>Bemerkungen

`GetControlHandle`ist eine Hilfsmethode, die das fensterhandle zurückgibt, das in den .NET Framework-Steuerelementeigenschaften gespeichert ist. Der Fensterhandlewert wird während des Aufrufs von [CWnd::Attach](../../mfc/reference/cwnd-class.md#attach)in [CWnd::m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) kopiert.

## <a name="cwinformscontroloperator--gt"></a><a name="operator_-_gt"></a>CWinFormsControl::operator -&gt;

Ersetzt [CWinFormsControl::GetControl](#getcontrol) in Ausdrücken.

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator stellt eine praktische `GetControl` Syntax bereit, die in Ausdrücken ersetzt wird.

Weitere Informationen zu Windows Forms finden Sie unter [Verwenden einer Windows Form-Benutzersteuerung in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformscontroloperator-tmanagedcontrol"></a><a name="operator_tmanagedcontrol"></a>CWinFormsControl::operator TManagedControl

Gibt einen Typ als Zeiger auf ein Windows Forms-Steuerelement um.

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator `CWinFormsControl<TManagedControl>` übergibt an Funktionen, die einen Zeiger auf ein Windows Forms-Steuerelement akzeptieren.

## <a name="see-also"></a>Siehe auch

[CWinFormsDialog-Klasse](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CWinFormsView-Klasse](../../mfc/reference/cwinformsview-class.md)
