---
title: Anwendungssteuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: cb4ad19dfad06b793f226324d8e28c37c084ad67
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855687"
---
# <a name="application-control"></a>Anwendungssteuerelement

OLE erfordert eine beträchtliche Kontrolle über Anwendungen und ihre Objekte. Die OLE-System-DLLs müssen in der Lage sein, Anwendungen automatisch zu starten und freizugeben, die Produktion und die Änderungen von Objekten zu koordinieren usw. Die Funktionen in diesem Thema erfüllen diese Anforderungen. Diese Funktionen müssen nicht nur von den OLE-System-DLLs aufgerufen werden, sondern auch von Anwendungen aufgerufen werden.

### <a name="application-control"></a>Anwendungssteuerelement

|||
|-|-|
|[Afxolecanexitapp](#afxolecanexitapp)|Gibt an, ob die Anwendung beendet werden kann.|
|[Afxolegetmessagefilter](#afxolegetmessagefilter)|Ruft den aktuellen Nachrichtenfilter der Anwendung ab.|
|[Afxolegetuserctrl](#afxolegetuserctrl)|Ruft das aktuelle benutzersteuerungsflag ab.|
|[Afxolesetuserctrl](#afxolesetuserctrl)|Legt das benutzersteuerungsflag fest oder löscht dieses.|
|[AfxOleLockApp](#afxolelockapp)|Inkremente die globale Anzahl der in einer Anwendung aktiven Objekte.|
|[Afxolelockcontrol](#afxolelockcontrol)| Sperrt die Klassenfactory des angegebenen Steuer Elements. |
|[AfxOleUnlockApp](#afxoleunlockapp)|Dekremente die Anzahl der aktiven Objekte in einer Anwendung in der frameworkanzahl.|
|[Afxoleunlockcontrol](#afxoleunlockcontrol)| Entsperrt die Klassenfactory des angegebenen Steuer Elements. |
|[Afxoleregisterserverclass](#afxoleregisterserverclass)|Registriert einen Server in der OLE-Systemregistrierung.|
|[Afxoleseteditmenu](#afxoleseteditmenu)|Implementiert die Benutzeroberfläche für den *Typname* -Objekt Befehl.|

##  <a name="afxolecanexitapp"></a>Afxolecanexitapp

Gibt an, ob die Anwendung beendet werden kann.

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die Anwendung beendet werden kann. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Eine Anwendung sollte nicht beendet werden, wenn ausstehende Verweise auf die Objekte vorhanden sind. Die globalen Funktionen `AfxOleLockApp` und `AfxOleUnlockApp` Inkrement-und Dekrement-Wert bzw. ein gegen Objekt der Verweise auf die Objekte der Anwendung. Die Anwendung sollte nicht beendet werden, wenn dieser Wert ungleich 0 (null) ist. Wenn der Wert ungleich 0 (null) ist, wird das Hauptfenster der Anwendung ausgeblendet (nicht zerstört), wenn der Benutzer im Menüsystem die Option schließen auswählt oder im Menü Datei auf Beenden klickt. Das Framework ruft diese Funktion in `CFrameWnd::OnClose`auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>Requirements (Anforderungen)

**Header**: afxdisp. h

##  <a name="afxolegetmessagefilter"></a>Afxolegetmessagefilter

Ruft den aktuellen Nachrichtenfilter der Anwendung ab.

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den aktuellen Nachrichtenfilter.

### <a name="remarks"></a>Bemerkungen

Diese Funktion aufrufen, um auf das aktuelle `COleMessageFilter`von abgeleitetes Objekt zuzugreifen, genauso wie Sie `AfxGetApp` aufrufen, um auf das aktuelle Anwendungs Objekt zuzugreifen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header**: AFXWIN. h

##  <a name="afxolegetuserctrl"></a>Afxolegetuserctrl

Ruft das aktuelle benutzersteuerungsflag ab.

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Benutzer die Kontrolle über die Anwendung hat. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Der Benutzer ist in der Lage, die Anwendung zu steuern, wenn der Benutzer ein neues Dokument explizit geöffnet oder erstellt hat. Der Benutzer ist auch dann in der Kontrolle, wenn die Anwendung nicht von den OLE-System-DLLs gestartet wurde – mit anderen Worten, wenn der Benutzer die Anwendung mit der systemshell gestartet hat.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header**: afxdisp. h

##  <a name="afxolesetuserctrl"></a>Afxolesetuserctrl

Legt das benutzersteuerungsflag fest, das in der Referenz für `AfxOleGetUserCtrl`erläutert wird, oder löscht dieses.

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>Parameter

*buserctrl*<br/>
Gibt an, ob das Benutzer Steuerelement-Flag festgelegt oder gelöscht werden soll.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Funktion auf, wenn der Benutzer ein Dokument erstellt oder lädt, jedoch nicht, wenn ein Dokument durch eine indirekte Aktion geladen oder erstellt wird, z. b. das Laden eines eingebetteten Objekts aus einer Containeranwendung.

Diese Funktion wird aufgerufen, wenn der Benutzer von anderen Aktionen in der Anwendung in die Kontrolle über die Anwendung versetzt werden soll.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header**: afxdisp. h

##  <a name="afxolelockapp"></a>AfxOleLockApp

Inkremente die globale Anzahl der in der Anwendung aktiven Objekte.

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>Bemerkungen

Das Framework behält die Anzahl der in einer Anwendung aktiven Objekte bei. Die Funktionen "`AfxOleLockApp`" und "`AfxOleUnlockApp`" erhöhen und Dekrement diese Anzahl.

Wenn der Benutzer versucht, eine Anwendung zu schließen, die über aktive Objekte verfügt – eine Anwendung, für die die Anzahl der aktiven Objekte ungleich 0 (null) ist – verbirgt das Framework die Anwendung aus der Ansicht des Benutzers, anstatt sie vollständig herunterzufahren. Die `AfxOleCanExitApp`-Funktion gibt an, ob die Anwendung beendet werden kann.

Ruft `AfxOleLockApp` von jedem Objekt auf, das OLE-Schnittstellen verfügbar macht, wenn es nicht wünschenswert ist, dass dieses Objekt zerstört wird, während es von einer Client Anwendung verwendet wird. Rufen Sie auch `AfxOleUnlockApp` im Dekonstruktor eines beliebigen Objekts auf, das `AfxOleLockApp` im Konstruktor aufruft. Standardmäßig Sperren und entsperren `COleDocument` (und abgeleiteten Klassen) die Anwendung automatisch.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header**: afxdisp. h

##  <a name="afxoleunlockapp"></a>AfxOleUnlockApp

Dekremente die Anzahl der aktiven Objekte in der Anwendung.

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter `AfxOleLockApp`.

Wenn die Anzahl aktiver Objekte NULL erreicht, wird `AfxOleOnReleaseAllObjects` aufgerufen.

### <a name="example"></a>Beispiel

Sehen Sie sich das Beispiel für [AfxOleLockApp](#afxolelockapp)an.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header**: afxdisp. h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

Sperrt die Klassenfactory des angegebenen Steuer Elements, sodass dynamisch erstellte Daten, die dem Steuerelement zugeordnet sind, im Arbeitsspeicher verbleiben.

### <a name="syntax"></a>Syntax

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parameter

*CLSID*<br/>
Die eindeutige Klassen-ID des Steuer Elements.

*lpszprogid*<br/>
Die eindeutige Programm-ID des Steuer Elements.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Klassenfactory des Steuer Elements erfolgreich gesperrt wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Dadurch kann die Anzeige der Steuerelemente erheblich beschleunigt werden. Wenn Sie z. b. ein Steuerelement in einem Dialogfeld erstellen und das Steuerelement mit `AfxOleLockControl`sperren, müssen Sie es nicht jedes Mal neu erstellen und beenden, wenn das Dialogfeld angezeigt oder zerstört wird. Wenn der Benutzer ein Dialogfeld wiederholt öffnet und schließt, kann das Sperren der Steuerelemente die Leistung erheblich verbessern. Wenn Sie bereit sind, das Steuerelement zu zerstören, wenden Sie `AfxOleUnlockControl`an.

### <a name="example"></a>Beispiel

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

##  <a name="afxoleregisterserverclass"></a>Afxoleregisterserverclass

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

*CLSID*<br/>
Verweis auf die OLE-Klassen-ID des Servers.

*lpszClassName*<br/>
Zeiger auf eine Zeichenfolge, die den Klassennamen der Objekte des Servers enthält.

*lpszshorttypame*<br/>
Zeiger auf eine Zeichenfolge, die den Kurznamen des Objekt Typs des Servers enthält, z. b. "Diagramm".

*lpszlongtypame*<br/>
Zeiger auf eine Zeichenfolge, die den langen Namen des Objekt Typs des Servers enthält, z. b. "Microsoft Excel 5,0-Diagramm".

*napptype*<br/>
Ein Wert aus der OLE_APPTYPE-Enumeration, der den Typ der OLE-Anwendung angibt. Folgende Werte sind möglich:

- OAT_INPLACE_SERVER Server verfügt über eine vollständige Server Benutzeroberfläche.

- OAT_SERVER Server unterstützt nur Einbettungen.

- OAT_CONTAINER Container unterstützt Links zu Einbettungen.

- OAT_DISPATCH_OBJECT `IDispatch`-fähigen Objekts.

*rglpszregister*<br/>
Array von Zeigern auf Zeichen folgen, die die Schlüssel und Werte darstellen, die der OLE-Systemregistrierung hinzugefügt werden sollen, wenn keine vorhandenen Werte für die Schlüssel gefunden werden.

*rglpszüberschreibung*<br/>
Array von Zeigern auf Zeichen folgen, die die Schlüssel und Werte darstellen, die der OLE-Systemregistrierung hinzugefügt werden sollen, wenn die Registrierung vorhandene Werte für die angegebenen Schlüssel enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Serverklasse erfolgreich registriert wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die meisten Anwendungen können `COleTemplateServer::Register` verwenden, um die Dokumenttypen der Anwendung zu registrieren. Wenn das System Registrierungs Format Ihrer Anwendung nicht mit dem typischen Muster kompatibel ist, können Sie `AfxOleRegisterServerClass` für mehr Kontrolle verwenden.

Die Registrierung besteht aus einem Satz von Schlüsseln und Werten. Die Argumente *rglpszregister* und *rglpszüberschreibung* sind Arrays von Zeigern auf Zeichen folgen, die jeweils aus einem Schlüssel und einem Wert bestehen, der durch ein **null** -Zeichen (`'\0'`) getrennt ist. Jede dieser Zeichen folgen kann ersetzbare Parameter haben, deren Positionen durch die Zeichen folgen *%1* bis *%5*gekennzeichnet sind.

Die Symbole werden wie folgt ausgefüllt:

|Symbol|value|
|------------|-----------|
|%1|Klassen-ID, formatiert als Zeichenfolge|
|%2|Klassenname|
|%3|Pfad zur ausführbaren Datei|
|%4|Kurztyp Name|
|%5|Name des langen Typs|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header**: afxdisp. h

##  <a name="afxoleseteditmenu"></a>Afxoleseteditmenu

Implementiert die Benutzeroberfläche für den *Typname* -Objekt Befehl.

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

*pclient*<br/>
Ein Zeiger auf das Client-OLE-Element.

*pmenu*<br/>
Ein Zeiger auf das zu Aktualisier Ende Menü Objekt.

*iMenuItem*<br/>
Der Index des zu aktualisierenden Menü Elements.

*nidverbmin*<br/>
Die Befehls-ID, die dem primären Verb entspricht.

*nidverbmax*<br/>
Die Befehls-ID, die dem letzten Verb entspricht.

*nidconvert*<br/>
ID für das Menü Element konvertieren.

### <a name="remarks"></a>Bemerkungen

Wenn der Server nur ein primäres Verb erkennt, wird das Menü Element zu "Verb *Typname* Object", und der Befehl " *nidverbmin* " wird gesendet, wenn der Benutzer den Befehl auswählt. Wenn der Server mehrere Verben erkennt, wird das Menü Element zu " *tykame* Object", und ein Untermenü mit allen Verben wird angezeigt, wenn der Benutzer den Befehl auswählt. Wenn der Benutzer ein Verb aus dem Untermenü auswählt, wird " *nidverbmin* " gesendet, wenn das erste Verb ausgewählt wird, " *transiverbmin* + 1" gesendet wird, wenn das zweite Verb ausgewählt ist usw. Diese Funktion wird von der standardmäßigen `COleDocument`-Implementierung automatisch verarbeitet.

Sie müssen über die folgende Anweisung im Anwendungs Ressourcen Skript Ihres Clients verfügen (. RC-Datei:

**#include \<AFXOLECL. RC >**

### <a name="requirements"></a>Requirements (Anforderungen)

**Header**: Afxole. h

## <a name="afxoleunlockcontrol"></a>Afxoleunlockcontrol

Entsperrt die Klassenfactory des angegebenen Steuer Elements.

### <a name="syntax"></a>Syntax

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parameter

*CLSID*<br/>
Die eindeutige Klassen-ID des Steuer Elements.

*lpszprogid*<br/>
Die eindeutige Programm-ID des Steuer Elements.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Klassenfactory des Steuer Elements erfolgreich entsperrt wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein Steuerelement ist mit `AfxOleLockControl`gesperrt, sodass dynamisch erstellte Daten, die dem Steuerelement zugeordnet sind, im Arbeitsspeicher verbleiben. Dadurch kann die Anzeige des Steuer Elements deutlich beschleunigt werden, da das Steuerelement nicht jedes Mal erstellt und zerstört werden muss, wenn es angezeigt wird. Wenn Sie bereit sind, das Steuerelement zu zerstören, wenden Sie `AfxOleUnlockControl`an.

### <a name="example"></a>Beispiel

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="see-also"></a>Weitere Informationen

[Makros und Globals](mfc-macros-and-globals.md)<br/>
