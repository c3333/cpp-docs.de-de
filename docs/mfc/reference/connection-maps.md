---
title: Verbindungszuordnungen
ms.date: 11/04/2016
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: 947cd09023ef4028a32db8e2e4e8b33f7e04e0dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374806"
---
# <a name="connection-maps"></a>Verbindungszuordnungen

OLE-Steuerelemente können Schnittstellen für andere Anwendungen verfügbar machen. Diese Schnittstellen erlauben nur den Zugriff von einem Container auf dieses Steuerelement. Wenn ein OLE-Steuerelement auf externe Schnittstellen anderer OLE-Objekte zugreifen möchte, muss ein Verbindungspunkt eingerichtet werden. Dieser Verbindungspunkt ermöglicht einen ausgehenden Zugriff auf externe Dispatchkarten, z. B. Ereigniszuordnungen oder Benachrichtigungsfunktionen.

Die Microsoft Foundation-Klassenbibliothek bietet ein Programmiermodell, das Verbindungspunkte unterstützt. In diesem Modell werden "Verbindungszuordnungen" verwendet, um Schnittstellen oder Verbindungspunkte für das OLE-Steuerelement festzulegen. Verbindungszuordnungen enthalten ein Makro für jeden Verbindungspunkt. Weitere Informationen zu Verbindungszuordnungen finden Sie in der [CConnectionPoint-Klasse.](../../mfc/reference/cconnectionpoint-class.md)

In der Regel unterstützt ein Steuerelement nur zwei Verbindungspunkte: einen für Ereignisse und einen für Eigenschaftsbenachrichtigungen. Diese werden von `COleControl` der Basisklasse implementiert und erfordern keine zusätzliche Arbeit durch den Steuerelementschreiber. Alle zusätzlichen Verbindungspunkte, die Sie in Ihrer Klasse implementieren möchten, müssen manuell hinzugefügt werden. Zur Unterstützung von Verbindungszuordnungen und -punkten stellt MFC die folgenden Makros bereit:

### <a name="connection-map-declaration-and-demarcation"></a>Verbindungszuordnungserklärung und Abgrenzung

|||
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|Deklariert eine eingebettete Klasse, die einen zusätzlichen Verbindungspunkt implementiert (muss in der Klassendeklaration verwendet werden).|
|[END_CONNECTION_PART](#end_connection_part)|Beendet die Deklaration eines Verbindungspunkts (muss in der Klassendeklaration verwendet werden).|
|[CONNECTION_IID](#connection_iid)|Gibt die Schnittstellen-ID des Verbindungspunkts des Steuerelements an.|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|Deklariert, dass eine Verbindungszuordnung in einer Klasse verwendet wird (muss in der Klassendeklaration verwendet werden).|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|Beginnt die Definition einer Verbindungszuordnung (muss in der Klassenimplementierung verwendet werden).|
|[END_CONNECTION_MAP](#end_connection_map)|Beendet die Definition einer Verbindungszuordnung (muss in der Klassenimplementierung verwendet werden).|
|[CONNECTION_PART](#connection_part)|Gibt einen Verbindungspunkt in der Verbindungszuordnung des Steuerelements an.|

Die folgenden Funktionen unterstützen eine Senke beim Herstellen und Trennen einer Verbindung mithilfe von Verbindungspunkten:

### <a name="initializationtermination-of-connection-points"></a>Initialisierung/Beendigung von Verbindungspunkten

|||
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|Stellt eine Verbindung zwischen einer Quelle und einer Senke her.|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|Unterbricht eine Verbindung zwischen einer Quelle und einer Senke.|

## <a name="begin_connection_part"></a><a name="begin_connection_part"></a>BEGIN_CONNECTION_PART

Verwenden Sie das BEGIN_CONNECTION_PART-Makros, um mit der Definition zusätzlicher Verbindungspunkte über die Ereignis- und Eigenschaftenbenachrichtigungsverbindungspunkte hinaus zu beginnen.

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Gibt den Namen der Steuerelementklasse an, deren Verbindungspunkt dies ist.

*localClass*<br/>
Gibt den Namen der lokalen Klasse an, die den Verbindungspunkt implementiert.

### <a name="remarks"></a>Bemerkungen

Starten Sie in der Deklarationsdatei (.h), die die Memberfunktionen für Ihre Klasse definiert, den Verbindungspunkt mit dem BEGIN_CONNECTION_PART-Makro, fügen Sie dann das CONNECTION_IID-Makro und alle anderen Memberfunktionen hinzu, die Sie implementieren möchten, und vervollständigen Sie die Verbindungspunktzuordnung mit dem END_CONNECTION_PART-Makro.

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="end_connection_part"></a><a name="end_connection_part"></a>END_CONNECTION_PART

Beendet die Deklaration Ihres Verbindungspunkts.

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>Parameter

*localClass*<br/>
Gibt den Namen der lokalen Klasse an, die den Verbindungspunkt implementiert.

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="connection_iid"></a><a name="connection_iid"></a>CONNECTION_IID

Verwenden Sie zwischen den makros BEGIN_CONNECTION_PART und END_CONNECTION_PART, um eine Schnittstellen-ID für einen Verbindungspunkt zu definieren, der von Ihrem OLE-Steuerelement unterstützt wird.

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
Die Schnittstellen-ID der Schnittstelle, die vom Verbindungspunkt aufgerufen wird.

### <a name="remarks"></a>Bemerkungen

Das *iid-Argument* ist eine Schnittstellen-ID, die verwendet wird, um die Schnittstelle zu identifizieren, die der Verbindungspunkt auf seine verbundenen Senken aufruft. Beispiel:

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

gibt einen Verbindungspunkt an, der die `ISinkInterface` Schnittstelle aufruft.

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="declare_connection_map"></a><a name="declare_connection_map"></a>DECLARE_CONNECTION_MAP

Jede `COleControl`-abgeleitete Klasse in Ihrem Programm kann eine Verbindungszuordnung bereitstellen, um zusätzliche Verbindungspunkte anzugeben, die vom Steuerelement unterstützt werden.

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>Bemerkungen

Wenn das Steuerelement zusätzliche Punkte unterstützt, verwenden Sie das DECLARE_CONNECTION_MAP-Makro am Ende der Klassendeklaration. Verwenden Sie dann in der CPP-Datei, die die Memberfunktionen für die Klasse definiert, das BEGIN_CONNECTION_MAP-Makro, CONNECTION_PART Makros für jeden Verbindungspunkt des Steuerelements und das END_CONNECTION_MAP-Makro, um das Ende der Verbindungszuordnung zu deklarieren.

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="begin_connection_map"></a><a name="begin_connection_map"></a>BEGIN_CONNECTION_MAP

Jede `COleControl`-abgeleitete Klasse in Ihrem Programm kann eine Verbindungszuordnung bereitstellen, um Verbindungspunkte anzugeben, die von Ihrem Steuerelement unterstützt werden.

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Gibt den Namen der Steuerelementklasse an, deren Verbindungszuordnung dies ist.

*theBase*<br/>
Gibt den Namen der Basisklasse *derKlasse*an.

### <a name="remarks"></a>Bemerkungen

In der Implementierung (. CPP)-Datei, die die Memberfunktionen für Ihre Klasse definiert, die Verbindungszuordnung mit dem BEGIN_CONNECTION_MAP-Makro [CONNECTION_PART](#connection_part) sanieren und dann Makroeinträge für jeden Ihrer Verbindungspunkte mithilfe des CONNECTION_PART-Makros hinzufügen. Vervollständigen Sie schließlich die [END_CONNECTION_MAP](#end_connection_map) Verbindungszuordnung mit dem END_CONNECTION_MAP-Makro.

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="end_connection_map"></a><a name="end_connection_map"></a>END_CONNECTION_MAP

Beendet die Definition der Verbindungszuordnung.

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="connection_part"></a><a name="connection_part"></a>CONNECTION_PART

Ordnet einen Verbindungspunkt für Ihr OLE-Steuerelement einer bestimmten Schnittstellen-ID zu.

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Gibt den Namen der Steuerelementklasse an, deren Verbindungspunkt dies ist.

*Iid*<br/>
Die Schnittstellen-ID der Schnittstelle, die vom Verbindungspunkt aufgerufen wird.

*localClass*<br/>
Gibt den Namen der lokalen Klasse an, die den Verbindungspunkt implementiert.

### <a name="remarks"></a>Bemerkungen

Beispiel:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

implementiert eine Verbindungszuordnung mit einem Verbindungspunkt, `IID_ISinkInterface` der die Schnittstelle aufruft.

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="afxconnectionadvise"></a><a name="afxconnectionadvise"></a>AfxConnectionAdvise

Rufen Sie diese Funktion auf, um eine Verbindung zwischen einer Quelle herzustellen, die von *pUnkSrc*angegeben wird, und einer Senke, die von *pUnkSink*angegeben wird.

```
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD FAR* pdwCookie);
```

### <a name="parameters"></a>Parameter

*pUnkSrc*<br/>
Ein Zeiger auf das Objekt, das die Schnittstelle aufruft.

*pUnkSink*<br/>
Ein Zeiger auf das Objekt, das die Schnittstelle implementiert.

*Iid*<br/>
Die Schnittstellen-ID der Verbindung.

*bRefCount*<br/>
TRUE gibt an, dass das Erstellen der Verbindung dazu führen soll, dass die Referenzanzahl von *pUnkSink* erhöht wird. FALSE gibt an, dass die Referenzanzahl nicht erhöht werden soll.

*pdwCookie*<br/>
Ein Zeiger auf ein DWORD, bei dem ein Verbindungsbezeichner zurückgegeben wird. Dieser Wert sollte als *dwCookie-Parameter* übergeben werden, wenn `AfxConnectionUnadvise` die Verbindung getrennt wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn eine Verbindung hergestellt wurde; andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afxctl.h

## <a name="afxconnectionunadvise"></a><a name="afxconnectionunadvise"></a>AfxConnectionUnadvise

Rufen Sie diese Funktion auf, um eine Verbindung zwischen einer Quelle, die von *pUnkSrc*angegeben wird, und einer Senke, die von *pUnkSink*angegeben wird, zu trennen.

```
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD dwCookie);
```

### <a name="parameters"></a>Parameter

*pUnkSrc*<br/>
Ein Zeiger auf das Objekt, das die Schnittstelle aufruft.

*pUnkSink*<br/>
Ein Zeiger auf das Objekt, das die Schnittstelle implementiert.

*Iid*<br/>
Die Schnittstellen-ID der Verbindungspunktschnittstelle.

*bRefCount*<br/>
TRUE gibt an, dass das Trennen der Verbindung dazu führen soll, dass die Referenzanzahl von *pUnkSink* verringert wird. FALSE gibt an, dass die Referenzanzahl nicht verringert werden soll.

*dwCookie*<br/>
Der Verbindungsbezeichner, der von `AfxConnectionAdvise`zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn eine Verbindung getrennt wurde; andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afxctl.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
