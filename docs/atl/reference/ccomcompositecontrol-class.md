---
title: CComCompositeControl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComCompositeControl
- ATLCTL/ATL::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::AdviseSinkMap
- ATLCTL/ATL::CComCompositeControl::CalcExtent
- ATLCTL/ATL::CComCompositeControl::Create
- ATLCTL/ATL::CComCompositeControl::CreateControlWindow
- ATLCTL/ATL::CComCompositeControl::SetBackgroundColorFromAmbient
- ATLCTL/ATL::CComCompositeControl::m_hbrBackground
- ATLCTL/ATL::CComCompositeControl::m_hWndFocus
helpviewer_keywords:
- CComCompositeControl class
- composite controls, CComCompositeControl class
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
ms.openlocfilehash: 700a8047ab1fa9df85c8e6530eb3eed5f29bd3d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320806"
---
# <a name="ccomcompositecontrol-class"></a>CComCompositeControl-Klasse

Diese Klasse stellt die Methoden bereit, die zum Implementieren eines zusammengesetzten Steuerelements erforderlich sind.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, abgeleitet von [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) oder [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), sowie von allen anderen Schnittstellen, die Sie für Ihr zusammengesetztes Steuerelement unterstützen möchten.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|Der Konstruktor.|
|[CComCompositeControl::'cComCompositeControl](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|Rufen Sie diese Methode auf, um alle Steuerelemente, die vom zusammengesetzten Steuerelement gehostet werden, zu beraten oder zu entberaten.|
|[CComCompositeControl::CalcExtent](#calcextent)|Rufen Sie diese Methode auf, um die Größe in HIMETRIC-Einheiten der Dialogressource zu berechnen, die zum Hosten des zusammengesetzten Steuerelements verwendet wird.|
|[CComCompositeControl::Erstellen](#create)|Diese Methode wird aufgerufen, um das Steuerfenster für das zusammengesetzte Steuerelement zu erstellen.|
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|Rufen Sie diese Methode auf, um das Steuerelementfenster zu erstellen und jedes gehostete Steuerelement zu beraten.|
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|Rufen Sie diese Methode auf, um die Hintergrundfarbe des zusammengesetzten Steuerelements mithilfe der Hintergrundfarbe des Containers festzulegen.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|Der Hintergrundpinsel.|
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|Das Handle des Fensters, das derzeit den Fokus hat.|

## <a name="remarks"></a>Bemerkungen

Von der `CComCompositeControl` Klasse abgeleitete Klassen erben die Funktionalität eines ActiveX-Verbundsteuerelements. Von einem Standarddialogfeld abgeleitete ActiveX-Steuerelemente `CComCompositeControl` werden von einem Standarddialogfeld gehostet. Diese Steuerelementtypen werden als zusammengesetzte Steuerelemente bezeichnet, da sie andere Steuerelemente hosten können (systemeigene Windows-Steuerelemente und ActiveX-Steuerelemente).

`CComCompositeControl`identifiziert die Dialogressource, die beim Erstellen des zusammengesetzten Steuerelements verwendet werden soll, indem nach einem aufgezählten Datenmember in der untergeordneten Klasse gesucht wird. Die Member-IDD dieser untergeordneten Klasse wird auf die Ressourcen-ID der Dialogressource festgelegt, die als Fenster des Steuerelements verwendet wird. Im Folgenden finden Sie ein Beispiel für `CComCompositeControl` den Datenmember, von dem die abgeleitete Klasse die Dialogressource enthalten soll, die für das Fenster des Steuerelements verwendet werden soll:

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
> Zusammengesetzte Steuerelemente sind immer Fenstersteuerelemente, obwohl sie fensterlose Steuerelemente enthalten können.

Ein Steuerelement, `CComCompositeControl`das von einer -derived-Klasse implementiert wurde, verfügt über ein integriertes Standard-Tabbing-Verhalten. Wenn das Steuerelement den Fokus erhält, indem es in einer enthaltenden Anwendung tabbed wird, führt das sukzessive Drücken der TAB-Taste dazu, dass der Fokus durch alle enthaltenen Steuerelemente des zusammengesetzten Steuerelements, dann a-out aus dem zusammengesetzten Steuerelement und weiter zum nächsten Element in der Tabstoppreihenfolge des Containers geleitet wird. Die Tab-Reihenfolge der gehosteten Steuerelemente wird von der Dialogressource bestimmt und bestimmt die Reihenfolge, in der die Registerkarten stattfinden.

> [!NOTE]
> Damit Beschleuniger ordnungsgemäß mit `CComCompositeControl`einem funktionieren, ist es notwendig, eine Beschleunigertabelle zu laden, wenn das Steuerelement erstellt wird, den Griff und die Anzahl der Beschleuniger zurück an [IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo)übergeben und schließlich die Tabelle zerstören, wenn das Steuerelement freigegeben wird.

## <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="ccomcompositecontroladvisesinkmap"></a><a name="advisesinkmap"></a>CComCompositeControl::AdviseSinkMap

Rufen Sie diese Methode auf, um alle Steuerelemente, die vom zusammengesetzten Steuerelement gehostet werden, zu beraten oder zu entberaten.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parameter

*bAdvise*<br/>
Stimmt, wenn alle Kontrollen zu beraten sind; ansonsten falsch.

### <a name="return-value"></a>Rückgabewert

|||
|-|-|
|S_OK  |Alle Steuerelemente in der Ereignissenkenzuordnung wurden erfolgreich mit ihrer Ereignisquelle verbunden oder getrennt.|
|E_FAIL  |Nicht alle Steuerelemente in der Ereignissenkenzuordnung konnten erfolgreich mit ihrer Ereignisquelle verbunden oder getrennt werden.|
|E_POINTER  |Dieser Fehler weist in der Regel auf ein Problem mit einem Eintrag in der `IDispEventImpl` `IDispEventSimpleImpl` Ereignissenkenzuordnung des Steuerelements oder auf ein Problem mit einem Vorlagenargument hin, das in einer oder einer Basisklasse verwendet wird.|
|CONNECT_E_ADVISELIMIT  |Der Verbindungspunkt hat bereits seine maximale Anzahl von Verbindungen erreicht und kann keine weiteren Verbindungen annehmen.|
|CONNECT_E_CANNOTCONNECT  |Die Senke unterstützt nicht die Schnittstelle, die für diesen Verbindungspunkt erforderlich ist.|
|CONNECT_E_NOCONNECTION  |Der Cookie-Wert stellt keine gültige Verbindung dar. Dieser Fehler weist in der Regel auf ein Problem mit einem Eintrag in der `IDispEventImpl` `IDispEventSimpleImpl` Ereignissenkenzuordnung des Steuerelements oder auf ein Problem mit einem Vorlagenargument hin, das in einer oder einer Basisklasse verwendet wird.|

### <a name="remarks"></a>Bemerkungen

Die Basisimplementierung dieser Methode durchsucht die Einträge in der Ereignissenkenzuordnung. Anschließend werden die Verbindungspunkte zu den COM-Objekten, die durch die Senkeneinträge der Ereignissenkenzuordnung beschrieben werden, empfohlen oder nicht empfohlen. Diese Membermethode basiert auch auf der Tatsache, dass die `IDispEventImpl` abgeleitete Klasse von einer Instanz für jedes Steuerelement in der Senkenzuordnung erbt, das beraten oder nicht empfohlen werden soll.

## <a name="ccomcompositecontrolcalcextent"></a><a name="calcextent"></a>CComCompositeControl::CalcExtent

Rufen Sie diese Methode auf, um die Größe in HIMETRIC-Einheiten der Dialogressource zu berechnen, die zum Hosten des zusammengesetzten Steuerelements verwendet wird.

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>Parameter

*Größe*<br/>
Ein Verweis `SIZE` auf eine Struktur, die mit dieser Methode gefüllt werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Steuerelement von einem Dialogfeld gehostet wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Die Größe wird im *Parameter "Größe"* zurückgegeben.

## <a name="ccomcompositecontrolcreate"></a><a name="create"></a>CComCompositeControl::Erstellen

Diese Methode wird aufgerufen, um das Steuerfenster für das zusammengesetzte Steuerelement zu erstellen.

```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parameter

*hWndEltern*<br/>
Ein Handle für das übergeordnete Fenster des Steuerelements.

*rcPos*<br/>
Reserviert.

*dwInitParam*<br/>
Daten, die während der Steuerelementerstellung an das Steuerelement übergeben werden sollen. Die als *dwInitParam* übergebenen Daten werden als LPARAM-Parameter der [WM_INITDIALOG-Nachricht](/windows/win32/dlgbox/wm-initdialog) angezeigt, die beim Erstellen an das zusammengesetzte Steuerelement gesendet wird.

### <a name="return-value"></a>Rückgabewert

Ein Handle für das neu erstellte Dialogfeld für zusammengesetzte Steuerelemente.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird normalerweise während der ortsgesteuerten Aktivierung des Steuerelements aufgerufen.

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="ccomcompositecontrol"></a>CComCompositeControl::CComCompositeControl

Der Konstruktor.

```
CComCompositeControl();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert die [Datenmember CComCompositeControl::m_hbrBackground](#m_hbrbackground) und [CComCompositeControl::m_hWndFocus](#m_hwndfocus) Datenmember auf NULL.

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="dtor"></a>CComCompositeControl::'cComCompositeControl

Der Destruktor.

```
~CComCompositeControl();
```

### <a name="remarks"></a>Bemerkungen

Löscht das Hintergrundobjekt, sofern vorhanden.

## <a name="ccomcompositecontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a>CComCompositeControl::CreateControlWindow

Rufen Sie diese Methode auf, um das Steuerelementfenster zu erstellen und alle gehosteten Steuerelemente zu beraten.

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>Parameter

*hWndEltern*<br/>
Ein Handle für das übergeordnete Fenster des Steuerelements.

*rcPos*<br/>
Das Positionsrechteck des zusammengesetzten Steuerelements in Clientkoordinaten relativ zu *hWndParent*.

### <a name="return-value"></a>Rückgabewert

Gibt ein Handle an das neu erstellte Dialogfeld für zusammengesetzte Steuerelemente zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [CComCompositeControl::Create](#create) und [CComCompositeControl::AdviseSinkMap](#advisesinkmap)auf.

## <a name="ccomcompositecontrolm_hbrbackground"></a><a name="m_hbrbackground"></a>CComCompositeControl::m_hbrBackground

Der Hintergrundpinsel.

```
HBRUSH m_hbrBackground;
```

## <a name="ccomcompositecontrolm_hwndfocus"></a><a name="m_hwndfocus"></a>CComCompositeControl::m_hWndFocus

Das Handle des Fensters, das derzeit den Fokus hat.

```
HWND m_hWndFocus;
```

## <a name="ccomcompositecontrolsetbackgroundcolorfromambient"></a><a name="setbackgroundcolorfromambient"></a>CComCompositeControl::SetBackgroundColorFromAmbient

Rufen Sie diese Methode auf, um die Hintergrundfarbe des zusammengesetzten Steuerelements mithilfe der Hintergrundfarbe des Containers festzulegen.

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="see-also"></a>Siehe auch

[CComControl-Klasse](../../atl/reference/ccomcontrol-class.md)<br/>
[Grundlagen von zusammengesetzten Steuerelementen](../../atl/atl-composite-control-fundamentals.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
