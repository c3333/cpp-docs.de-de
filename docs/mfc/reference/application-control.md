---
title: Anwendungssteuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: 1f438d3344e90a16def2bd4c0f9cedcd47a64203
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363555"
---
# <a name="application-control"></a>Anwendungssteuerelement

OLE erfordert eine umfassende Kontrolle über Anwendungen und deren Objekte. Die OLE-System-DLLs müssen in der Lage sein, Anwendungen automatisch zu starten und freizugeben, ihre Produktion und Änderung von Objekten zu koordinieren usw. Die Funktionen in diesem Thema erfüllen diese Anforderungen. Diese Funktionen werden nicht nur von den OLE-System-DLLs aufgerufen, sondern müssen manchmal auch von Anwendungen aufgerufen werden.

### <a name="application-control"></a>Anwendungssteuerelement

|||
|-|-|
|[AfxOleCanExitApp](#afxolecanexitapp)|Gibt an, ob die Anwendung beendet werden kann.|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|Ruft den aktuellen Nachrichtenfilter der Anwendung ab.|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|Ruft das aktuelle Benutzersteuerungsflag ab.|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|Legt das Benutzersteuerungsflag fest oder löscht es.|
|[AfxOleLockApp](#afxolelockapp)|Erhöht die globale Anzahl der aktiven Objekte in einer Anwendung.|
|[AfxOleLockControl](#afxolelockcontrol)| Sperrt die Klassenfactory des angegebenen Steuerelements. |
|[AfxOleUnlockApp](#afxoleunlockapp)|Dekrementiert die Anzahl der aktiven Objekte in einer Anwendung.|
|[AfxOleUnlockControl](#afxoleunlockcontrol)| Schaltet die Klassenfactory des angegebenen Steuerelements frei. |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|Registriert einen Server in der OLE-Systemregistrierung.|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|Implementiert die Benutzeroberfläche für den *Befehl typename* Object.|

## <a name="afxolecanexitapp"></a><a name="afxolecanexitapp"></a>AfxOleCanExitApp

Gibt an, ob die Anwendung beendet werden kann.

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Anwendung beendet werden kann; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Eine Anwendung sollte nicht beendet werden, wenn auf ihre Objekte verweise. Die globalen `AfxOleLockApp` `AfxOleUnlockApp` Funktionen und inkrementieren bzw. dekrementieren einen Zähler mit Verweisen auf die Objekte der Anwendung. Die Anwendung sollte nicht beendet werden, wenn dieser Leistungsindikator ungleich Null ist. Wenn der Leistungsindikator ungleich Null ist, wird das Hauptfenster der Anwendung ausgeblendet (nicht zerstört), wenn der Benutzer aus dem Systemmenü Schließen oder Aus dem Menü Datei beenden wählt. Das Framework ruft `CFrameWnd::OnClose`diese Funktion in auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>Anforderungen

**Kopfzeile**: afxdisp.h

## <a name="afxolegetmessagefilter"></a><a name="afxolegetmessagefilter"></a>AfxOleGetMessageFilter

Ruft den aktuellen Nachrichtenfilter der Anwendung ab.

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den aktuellen Nachrichtenfilter.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion `COleMessageFilter`auf, um auf das `AfxGetApp` aktuelle -abgeleitete Objekt zuzugreifen, genau wie Sie den Zugriff auf das aktuelle Anwendungsobjekt aufrufen würden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopfzeile**: afxwin.h

## <a name="afxolegetuserctrl"></a><a name="afxolegetuserctrl"></a>AfxOleGetUserCtrl

Ruft das aktuelle Benutzersteuerungsflag ab.

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Benutzer die Kontrolle über die Anwendung hat; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Der Benutzer hat die Kontrolle über die Anwendung, wenn der Benutzer ein neues Dokument explizit geöffnet oder erstellt hat. Der Benutzer hat auch die Kontrolle, wenn die Anwendung nicht von den OLE-System-DLLs gestartet wurde, d. h., wenn der Benutzer die Anwendung mit der Systemshell gestartet hat.

### <a name="requirements"></a>Anforderungen

**Kopfzeile**: afxdisp.h

## <a name="afxolesetuserctrl"></a><a name="afxolesetuserctrl"></a>AfxOleSetUserCtrl

Legt das Benutzersteuerungsflag fest oder löscht es, `AfxOleGetUserCtrl`das in der Referenz für erläutert wird.

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>Parameter

*bUserCtrl*<br/>
Gibt an, ob das Benutzersteuerungsflag festgelegt oder gelöscht werden soll.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Funktion auf, wenn der Benutzer ein Dokument erstellt oder lädt, jedoch nicht, wenn ein Dokument durch eine indirekte Aktion geladen oder erstellt wird, z. B. das Laden eines eingebetteten Objekts aus einer Containeranwendung.

Rufen Sie diese Funktion auf, wenn andere Aktionen in Ihrer Anwendung den Benutzer die Kontrolle über die Anwendung behalten sollen.

### <a name="requirements"></a>Anforderungen

**Kopfzeile**: afxdisp.h

## <a name="afxolelockapp"></a><a name="afxolelockapp"></a>AfxOleLockApp

Erhöht die globale Anzahl der aktiven Objekte in der Anwendung.

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>Bemerkungen

Das Framework enthält die Anzahl der Objekte, die in einer Anwendung aktiv sind. Die `AfxOleLockApp` `AfxOleUnlockApp` und Funktionen erhöhen bzw. dekrementieren diese Anzahl.

Wenn der Benutzer versucht, eine Anwendung mit aktiven Objekten zu schließen – eine Anwendung, für die die Anzahl der aktiven Objekte ungleich Null ist – blendet das Framework die Anwendung aus der Ansicht des Benutzers aus, anstatt sie vollständig herunterzufahren. Die `AfxOleCanExitApp` Funktion gibt an, ob die Anwendung beendet werden kann.

Aufruf `AfxOleLockApp` von jedem Objekt, das OLE-Schnittstellen verfügbar macht, wenn es nicht wünschenswert wäre, dass dieses Objekt zerstört wird, während es weiterhin von einer Clientanwendung verwendet wird. Rufen `AfxOleUnlockApp` Sie auch den Destruktor `AfxOleLockApp` eines Objekts auf, das im Konstruktor aufruft. Standardmäßig `COleDocument` sperren und entsperren (und abgeleitete Klassen) die Anwendung automatisch.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopfzeile**: afxdisp.h

## <a name="afxoleunlockapp"></a><a name="afxoleunlockapp"></a>AfxOleUnlockApp

Dekrementiert die Anzahl der aktiven Objekte in der Anwendung.

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>Bemerkungen

Weitere `AfxOleLockApp` Informationen finden Sie unter.

Wenn die Anzahl der aktiven `AfxOleOnReleaseAllObjects` Objekte Null erreicht, wird aufgerufen.

### <a name="example"></a>Beispiel

Siehe Beispiel für [AfxOleLockApp](#afxolelockapp).

### <a name="requirements"></a>Anforderungen

**Kopfzeile**: afxdisp.h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

Sperrt die Klassenfactory des angegebenen Steuerelements, sodass dynamisch erstellte Daten, die dem Steuerelement zugeordnet sind, im Arbeitsspeicher verbleiben.

### <a name="syntax"></a>Syntax

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parameter

*clsid*<br/>
Die eindeutige Klassen-ID des Steuerelements.

*lpszProgID*<br/>
Die eindeutige Programm-ID des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Klassenfabrik des Steuerelements erfolgreich gesperrt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Dies kann die Anzeige der Bedienelemente erheblich beschleunigen. Wenn Sie z. B. ein Steuerelement in einem `AfxOleLockControl`Dialogfeld erstellen und das Steuerelement mit sperren, müssen Sie es nicht jedes Mal erstellen und erneut töten, wenn das Dialogfeld angezeigt oder zerstört wird. Wenn der Benutzer ein Dialogfeld wiederholt öffnet und schließt, kann das Sperren der Steuerelemente die Leistung erheblich verbessern. Wenn Sie bereit sind, das `AfxOleUnlockControl`Steuerelement zu zerstören, rufen Sie an.

### <a name="example"></a>Beispiel

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="afxoleregisterserverclass"></a><a name="afxoleregisterserverclass"></a>AfxOleRegisterServerClass

Mit dieser Funktion können Sie Ihren Server in der OLE-Systemregistrierung registrieren.

```
BOOL AFXAPI AfxOleRegisterServerClass(
    REFCLSID clsid,
    LPCTSTR lpszClassName,
    LPCTSTR lpszShortTypeName,
    LPCTSTR lpszLongTypeName,
    OLE_APPTYPE nAppType = OAT_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL);
```

### <a name="parameters"></a>Parameter

*clsid*<br/>
Verweis auf die OLE-Klassen-ID des Servers.

*lpszClassName*<br/>
Zeiger auf eine Zeichenfolge, die den Klassennamen der Serverobjekte enthält.

*lpszShortTypeName*<br/>
Zeiger auf eine Zeichenfolge, die den Kurznamen des Objekttyps des Servers enthält, z. B. "Diagramm".

*lpszLongTypeName*<br/>
Zeiger auf eine Zeichenfolge, die den langen Namen des Objekttyps des Servers enthält, z. B. "Microsoft Excel 5.0 Diagramm".

*nAppType*<br/>
Ein Wert, der der OLE_APPTYPE-Enumeration entnommen wird und den Typ der OLE-Anwendung angibt. Mögliche Werte sind die folgenden:

- OAT_INPLACE_SERVER Server verfügt über eine vollständige Server-Benutzeroberfläche.

- OAT_SERVER Server unterstützt nur das Einbetten.

- OAT_CONTAINER Container unterstützt Links zu Einbettungen.

- OAT_DISPATCH_OBJECT `IDispatch`-fähiges Objekt.

*rglpszRegister*<br/>
Array von Zeigern auf Zeichenfolgen, die die Schlüssel und Werte darstellen, die der OLE-Systemregistrierung hinzugefügt werden sollen, wenn keine vorhandenen Werte für die Schlüssel gefunden werden.

*rglpszOverwrite*<br/>
Array von Zeigern auf Zeichenfolgen, die die Schlüssel und Werte darstellen, die der OLE-Systemregistrierung hinzugefügt werden sollen, wenn die Registrierung vorhandene Werte für die angegebenen Schlüssel enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Serverklasse erfolgreich registriert wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die meisten `COleTemplateServer::Register` Anwendungen können die Dokumenttypen der Anwendung registrieren. Wenn das Systemregistrierungsformat Ihrer Anwendung nicht zum typischen `AfxOleRegisterServerClass` Muster passt, können Sie mehr Steuerelemente verwenden.

Die Registrierung besteht aus einer Reihe von Schlüsseln und Werten. Die Argumente *rglpszRegister* und *rglpszOverwrite* sind Arrays von Zeigern auf Zeichenfolgen, die jeweils `'\0'`aus einem Schlüssel und einem Wert bestehen, der durch ein **NULL-Zeichen** ( ) getrennt ist. Jede dieser Zeichenfolgen kann über austauschbare Parameter verfügen, deren Stellen durch die Zeichenfolgen *%1* bis *%5*gekennzeichnet sind.

Die Symbole werden wie folgt ausgefüllt:

|Symbol|Wert|
|------------|-----------|
|%1|Klassen-ID, formatiert als Zeichenfolge|
|%2|Klassenname|
|%3|Pfad zur ausführbaren Datei|
|%4|Kurzer Typname|
|%5|Langer Typname|

### <a name="requirements"></a>Anforderungen

**Kopfzeile**: afxdisp.h

## <a name="afxoleseteditmenu"></a><a name="afxoleseteditmenu"></a>AfxOleSetEditMenu

Implementiert die Benutzeroberfläche für den *Befehl typename* Object.

```
void AFXAPI AfxOleSetEditMenu(
    COleClientItem* pClient,
    CMenu* pMenu,
    UINT iMenuItem,
    UINT nIDVerbMin,
    UINT nIDVerbMax = 0,
    UINT nIDConvert = 0);
```

### <a name="parameters"></a>Parameter

*pClient*<br/>
Ein Zeiger auf das CLIENT-OLE-Element.

*pMenu*<br/>
Ein Zeiger auf das zu aktualisierende Menüobjekt.

*iMenuItem*<br/>
Der Index des zu aktualisierenden Menüelements.

*nIDVerbMin*<br/>
Die Befehls-ID, die dem primären Verb entspricht.

*nIDVerbMax*<br/>
Die Befehls-ID, die dem letzten Verb entspricht.

*nIDConvert*<br/>
ID für das Menüelement Konvertieren.

### <a name="remarks"></a>Bemerkungen

Wenn der Server nur ein primäres Verb erkennt, wird das Menüelement zu "verb *typename* Object" und der Befehl *nIDVerbMin* wird gesendet, wenn der Benutzer den Befehl auswählt. Wenn der Server mehrere Verben erkennt, wird das Menüelement zu *"Typname-Objekt"* und ein Untermenü, das alle Verben auflistet, wenn der Benutzer den Befehl auswählt. Wenn der Benutzer ein Verb aus dem Untermenü auswählt, wird *nIDVerbMin* gesendet, wenn das erste Verb ausgewählt ist, *nIDVerbMin* + 1 wird gesendet, wenn das zweite Verb ausgewählt ist, und so weiter. Die `COleDocument` Standardimplementierung verarbeitet diese Funktion automatisch.

Sie müssen die folgende Anweisung im Anwendungsressourcenskript Ihres Clients (. RC)-Datei:

**#include \<afxolecl.rc>**

### <a name="requirements"></a>Anforderungen

**Kopfzeile**: afxole.h

## <a name="afxoleunlockcontrol"></a><a name="afxoleunlockcontrol"></a>AfxOleUnlockControl

Schaltet die Klassenfactory des angegebenen Steuerelements frei.

### <a name="syntax"></a>Syntax

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parameter

*clsid*<br/>
Die eindeutige Klassen-ID des Steuerelements.

*lpszProgID*<br/>
Die eindeutige Programm-ID des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Klassenfabrik des Steuerelements erfolgreich entsperrt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein Steuerelement ist `AfxOleLockControl`mit gesperrt, sodass dynamisch erstellte Daten, die dem Steuerelement zugeordnet sind, im Arbeitsspeicher verbleiben. Dies kann die Anzeige des Steuerelements erheblich beschleunigen, da das Steuerelement nicht jedes Mal erstellt und zerstört werden muss, wenn es angezeigt wird. Wenn Sie bereit sind, das `AfxOleUnlockControl`Steuerelement zu zerstören, rufen Sie an.

### <a name="example"></a>Beispiel

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)<br/>
