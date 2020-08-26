---
title: Verbindungszuordnungen
ms.date: 11/04/2016
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: 517017e9e60b86e96daa24f7822538e91c609fb4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841414"
---
# <a name="connection-maps"></a>Verbindungszuordnungen

OLE-Steuerelemente können Schnittstellen für andere Anwendungen verfügbar machen. Diese Schnittstellen ermöglichen nur den Zugriff von einem Container in dieses Steuerelement. Wenn ein OLE-Steuerelement auf externe Schnittstellen anderer OLE-Objekte zugreifen möchte, muss ein Verbindungspunkt eingerichtet werden. Dieser Verbindungspunkt ermöglicht das Steuern des ausgehenden Zugriffs auf externe Dispatchzuordnungen, z. b. Ereignis Zuordnungen oder Benachrichtigungsfunktionen.

Der Microsoft Foundation Class-Bibliothek bietet ein Programmiermodell, das Verbindungspunkte unterstützt. In diesem Modell werden "Verbindungs Zuordnungen" verwendet, um Schnittstellen oder Verbindungspunkte für das OLE-Steuerelement festzulegen. Verbindungs Zuordnungen enthalten ein Makro für jeden Verbindungspunkt. Weitere Informationen zu Verbindungs Zuordnungen finden Sie unter der [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) -Klasse.

In der Regel unterstützt ein Steuerelement nur zwei Verbindungspunkte: eines für Ereignisse und eines für Eigenschafts Benachrichtigungen. Diese werden von der `COleControl` -Basisklasse implementiert und erfordern keine zusätzliche Arbeit durch den Steuerelement-Writer. Alle zusätzlichen Verbindungspunkte, die Sie in der Klasse implementieren möchten, müssen manuell hinzugefügt werden. Um Verbindungs Zuordnungen und Punkte zu unterstützen, stellt MFC die folgenden Makros bereit:

### <a name="connection-map-declaration-and-demarcation"></a>Deklaration und Abgrenzung der Verbindungs Zuordnung

|Name|Beschreibung|
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|Deklariert eine eingebettete Klasse, die einen zusätzlichen Verbindungspunkt implementiert (muss in der Klassen Deklaration verwendet werden).|
|[END_CONNECTION_PART](#end_connection_part)|Beendet die Deklaration eines Verbindungs Punkts (muss in der Klassen Deklaration verwendet werden).|
|[CONNECTION_IID](#connection_iid)|Gibt die Schnittstellen-ID des Verbindungs Punkts des Steuer Elements an.|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|Deklariert, dass eine Verbindungs Zuordnung in einer Klasse verwendet wird (muss in der Klassen Deklaration verwendet werden).|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|Beginnt die Definition einer Verbindungs Zuordnung (muss in der Klassen Implementierung verwendet werden).|
|[END_CONNECTION_MAP](#end_connection_map)|Beendet die Definition einer Verbindungs Zuordnung (muss in der Klassen Implementierung verwendet werden).|
|[CONNECTION_PART](#connection_part)|Gibt einen Verbindungspunkt in der Verbindungs Zuordnung des-Steuer Elements an.|

Die folgenden Funktionen unterstützen eine Senke beim Einrichten und Trennen einer Verbindung mithilfe von Verbindungs Punkten:

### <a name="initializationtermination-of-connection-points"></a>Initialisierung/Beendigung von Verbindungs Punkten

|Name|Beschreibung|
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|Stellt eine Verbindung zwischen einer Quelle und einer Senke her.|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|Unterbricht eine Verbindung zwischen einer Quelle und einer Senke.|

## <a name="begin_connection_part"></a><a name="begin_connection_part"></a> BEGIN_CONNECTION_PART

Verwenden Sie das BEGIN_CONNECTION_PART-Makro, um die Definition zusätzlicher Verbindungspunkte zu starten, die über die Verbindungspunkte für Ereignisse und Verbindungspunkte hinausgehen.

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Gibt den Namen der Steuerelement Klasse an, deren Verbindungspunkt ist.

*localclass*<br/>
Gibt den Namen der lokalen Klasse an, die den Verbindungspunkt implementiert.

### <a name="remarks"></a>Bemerkungen

Starten Sie in der Deklarations Datei (. h), die die Element Funktionen für die Klasse definiert, den Verbindungspunkt mit dem BEGIN_CONNECTION_PART-Makro, fügen Sie dann das CONNECTION_IID Makro und alle anderen zu implementierenden Element Funktionen hinzu, und vervollständigen Sie die Verbindungspunkt Zuordnung mit dem END_CONNECTION_PART-Makro.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="end_connection_part"></a><a name="end_connection_part"></a> END_CONNECTION_PART

Beendet die Deklaration Ihres Verbindungs Punkts.

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>Parameter

*localclass*<br/>
Gibt den Namen der lokalen Klasse an, die den Verbindungspunkt implementiert.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="connection_iid"></a><a name="connection_iid"></a> CONNECTION_IID

Verwenden Sie zwischen dem BEGIN_CONNECTION_PART und END_CONNECTION_PART Makros, um eine Schnittstellen-ID für einen Verbindungspunkt zu definieren, der von Ihrem OLE-Steuerelement unterstützt

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>Parameter

*IID*<br/>
Die Schnittstellen-ID der Schnittstelle, die vom Verbindungspunkt aufgerufen wird.

### <a name="remarks"></a>Bemerkungen

Das *IID* -Argument ist eine Schnittstellen-ID, die verwendet wird, um die Schnittstelle zu identifizieren, die der Verbindungspunkt für seine verbundenen senken aufruft. Beispiel:

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

Gibt einen Verbindungspunkt an, der die- `ISinkInterface` Schnittstelle aufruft.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="declare_connection_map"></a><a name="declare_connection_map"></a> DECLARE_CONNECTION_MAP

Jede `COleControl` von abgeleitete Klasse in Ihrem Programm kann eine Verbindungs Zuordnung bereitstellen, um zusätzliche Verbindungspunkte anzugeben, die das Steuerelement unterstützt.

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>Bemerkungen

Wenn das Steuerelement zusätzliche Punkte unterstützt, verwenden Sie das DECLARE_CONNECTION_MAP-Makro am Ende der Klassen Deklaration. Verwenden Sie dann in der CPP-Datei, die die Element Funktionen für die-Klasse definiert, das BEGIN_CONNECTION_MAP-Makro, CONNECTION_PART Makros für jeden der Verbindungspunkte des Steuer Elements und das END_CONNECTION_MAP-Makro, um das Ende der Verbindungs Zuordnung zu deklarieren.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="begin_connection_map"></a><a name="begin_connection_map"></a> BEGIN_CONNECTION_MAP

Jede `COleControl` von abgeleitete Klasse in Ihrem Programm kann eine Verbindungs Zuordnung bereitstellen, um Verbindungspunkte anzugeben, die das Steuerelement unterstützt.

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Gibt den Namen der Steuerelement Klasse an, deren Verbindungs Zuordnung lautet.

*die Basis*<br/>
Gibt den Namen der Basisklasse von *TheClass*an.

### <a name="remarks"></a>Bemerkungen

In der-Implementierung (. Cpp-Datei, die die Member-Funktionen für die Klasse definiert, die Verbindungs Zuordnung mit dem BEGIN_CONNECTION_MAP-Makro startet und dann mithilfe des [CONNECTION_PART](#connection_part) -Makros Makro Einträge für jeden der Verbindungspunkte hinzuzufügen. Vervollständigen Sie schließlich die Verbindungs Zuordnung mit dem [END_CONNECTION_MAP](#end_connection_map) -Makro.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="end_connection_map"></a><a name="end_connection_map"></a> END_CONNECTION_MAP

Beendet die Definition der Verbindungs Zuordnung.

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="connection_part"></a><a name="connection_part"></a> CONNECTION_PART

Ordnet einen Verbindungspunkt für das OLE-Steuerelement einer bestimmten Schnittstellen-ID zu.

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Gibt den Namen der Steuerelement Klasse an, deren Verbindungspunkt ist.

*IID*<br/>
Die Schnittstellen-ID der Schnittstelle, die vom Verbindungspunkt aufgerufen wird.

*localclass*<br/>
Gibt den Namen der lokalen Klasse an, die den Verbindungspunkt implementiert.

### <a name="remarks"></a>Bemerkungen

Beispiel:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

implementiert eine Verbindungs Zuordnung mit einem Verbindungspunkt, der die- `IID_ISinkInterface` Schnittstelle aufruft.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="afxconnectionadvise"></a><a name="afxconnectionadvise"></a> Afxconnectionempfehlung

Mit dieser Funktion können Sie eine Verbindung zwischen einer durch *punksrc*angegebenen Quelle und einer Senke herstellen, die von *punksink*angegeben wird.

```
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD FAR* pdwCookie);
```

### <a name="parameters"></a>Parameter

*punksrc*<br/>
Ein Zeiger auf das Objekt, das die-Schnittstelle aufruft.

*punksink*<br/>
Ein Zeiger auf das Objekt, das die-Schnittstelle implementiert.

*IID*<br/>
Die Schnittstellen-ID der Verbindung.

*BREF count*<br/>
TRUE gibt an, dass das Erstellen der Verbindung bewirken soll, dass der Verweis Zähler von *punksink* inkrementiert wird. FALSE gibt an, dass der Verweis Zähler nicht inkrementiert werden soll.

*pdwcookie*<br/>
Ein Zeiger auf ein DWORD, bei dem ein Verbindungs Bezeichner zurückgegeben wird. Dieser Wert sollte als *dwCookie* -Parameter an übergeben werden, `AfxConnectionUnadvise` Wenn die Verbindung getrennt wird.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn eine Verbindung hergestellt wurde. andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxctl. h

## <a name="afxconnectionunadvise"></a><a name="afxconnectionunadvise"></a> Afxconnectionunrat

Mit dieser Funktion können Sie eine Verbindung zwischen einer durch *punksrc*angegebenen Quelle und einer Senke trennen, die von *punksink*angegeben wird.

```
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD dwCookie);
```

### <a name="parameters"></a>Parameter

*punksrc*<br/>
Ein Zeiger auf das Objekt, das die-Schnittstelle aufruft.

*punksink*<br/>
Ein Zeiger auf das Objekt, das die-Schnittstelle implementiert.

*IID*<br/>
Die Schnittstellen-ID der Verbindungspunkt Schnittstelle.

*BREF count*<br/>
TRUE gibt an, dass das Trennen der Verbindung dazu führen soll, dass der Verweis Zähler von *punksink* dekrementiert wird. FALSE gibt an, dass der Verweis Zähler nicht dekrementiert werden soll.

*dwCookie*<br/>
Der von zurückgegebene Verbindungs Bezeichner `AfxConnectionAdvise` .

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn eine Verbindung getrennt wurde. andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxctl. h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
