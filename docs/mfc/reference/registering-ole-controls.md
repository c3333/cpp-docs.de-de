---
title: Registrieren des OLE-Steuerelements
ms.date: 11/04/2016
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 2f2d7872e8b9369b5eef283e5b52a54c29afd563
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372971"
---
# <a name="registering-ole-controls"></a>Registrieren des OLE-Steuerelements

AUF OLE-Steuerelemente kann wie andere OLE-Serverobjekte auch andere OLE-fähige Anwendungen zugreifen. Dies wird durch die Registrierung der Typbibliothek und -klasse des Steuerelements erreicht.

Mit den folgenden Funktionen können Sie die Klasse, Eigenschaftenseiten und Typbibliothek des Steuerelements in der Windows-Registrierungsdatenbank hinzufügen und entfernen:

### <a name="registering-ole-controls"></a>Registrieren des OLE-Steuerelements

|||
|-|-|
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|Fügt die Klasse des Steuerelements zur Registrierungsdatenbank hinzu.|
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|Fügt der Registrierungsdatenbank eine Steuerelementeigenschaftsseite hinzu.|
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|Fügt der Registrierungsdatenbank die Typbibliothek des Steuerelements hinzu.|
|[AfxOleUnregisterClass](#afxoleunregisterclass)|Entfernt eine Steuerelementklasse oder eine Eigenschaftenseitenklasse aus der Registrierungsdatenbank.|
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|Entfernt die Typbibliothek des Steuerelements aus der Registrierungsdatenbank.|

`AfxOleRegisterTypeLib`wird in der Regel in einer `DllRegisterServer`Kontroll-DLL-Implementierung von aufgerufen. In `AfxOleUnregisterTypeLib` ähnlicher Weise `DllUnregisterServer`wird von aufgerufen. `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`und `AfxOleUnregisterClass` werden in `UpdateRegistry` der Regel von der Memberfunktion der Klassenfabrik oder Eigenschaftenseite eines Steuerelements aufgerufen.

## <a name="afxoleregistercontrolclass"></a><a name="afxoleregistercontrolclass"></a>AfxOleRegisterControlClass

Registriert die Steuerklasse bei der Windows-Registrierungsdatenbank.

```
BOOL AFXAPI AfxOleRegisterControlClass(
    HINSTANCE hInstance,
    REFCLSID clsid,
    LPCTSTR pszProgID,
    UINT idTypeName,
    UINT idBitmap,
    int nRegFlags,
    DWORD dwMiscStatus,
    REFGUID tlid,
    WORD wVerMajor,
    WORD wVerMinor);
```

### <a name="parameters"></a>Parameter

*hInstance*<br/>
Das Instanzhandle des Moduls, das der Steuerelementklasse zugeordnet ist.

*clsid*<br/>
Die eindeutige Klassen-ID des Steuerelements.

*pszProgID*<br/>
Die eindeutige Programm-ID des Steuerelements.

*idTypeName*<br/>
Die Ressourcen-ID der Zeichenfolge, die einen benutzerlesbaren Typnamen für das Steuerelement enthält.

*idBitmap*<br/>
Die Ressourcen-ID der Bitmap, die verwendet wird, um das OLE-Steuerelement in einer Symbolleiste oder Palette darzustellen.

*nRegFlags*<br/>
Enthält eines oder mehrere der folgenden Flags:

- `afxRegInsertable`Lässt das Steuerelement im Dialogfeld Objekt einfügen für OLE-Objekte angezeigt werden.

- `afxRegApartmentThreading`Legt das Threadingmodell in der Registrierung auf ThreadingModel=Apartment fest.

- `afxRegFreeThreading`Legt das Threadingmodell in der Registrierung auf ThreadingModel=Free fest.

   Sie können die `afxRegApartmentThreading` beiden `afxRegFreeThreading` Flags kombinieren und ThreadingModel=Both festlegen. Weitere Informationen zur Threadingmodellregistrierung finden Sie unter [InprocServer32](/windows/win32/com/inprocserver32) im Windows SDK.

> [!NOTE]
> In MFC-Versionen vor MFC 4.2 war der Parameter **int** *nRegFlags* ein BOOL-Parameter, *bInsertable*, der das Einfügen des Steuerelements aus dem Dialogfeld Objekt einfügen erlaubte oder nicht zuließ.

*dwMiscStatus*<br/>
Enthält eines oder mehrere der folgenden Statusflags (eine Beschreibung der Flags finden Sie unter OLEMISC-Enumeration im Windows SDK):

- OLEMISC_RECOMPOSEONRESIZE

- OLEMISC_ONLYICONIC

- OLEMISC_INSERTNOTREPLACE

- OLEMISC_STATIC

- OLEMISC_CANTLINKINSIDE

- OLEMISC_CANLINKBYOLE1

- OLEMISC_ISLINKOBJECT

- OLEMISC_INSIDEOUT

- OLEMISC_ACTIVATEWHENVISIBLE

- OLEMISC_RENDERINGISDEVICEINDEPENDENT

- OLEMISC_INVISIBLEATRUNTIME

- OLEMISC_ALWAYSRUN

- OLEMISC_ACTSLIKEBUTTON

- OLEMISC_ACTSLIKELABEL

- OLEMISC_NOUIACTIVATE

- OLEMISC_ALIGNABLE

- OLEMISC_IMEMODE

- OLEMISC_SIMPLEFRAME

- OLEMISC_SETCLIENTSITEFIRST

*tlid*<br/>
Die eindeutige ID der Steuerelementklasse.

*wVerMajor*<br/>
Die Hauptversionsnummer der Steuerungsklasse.

*wVerMinor*<br/>
Die Nebenversionsnummer der Steuerelementklasse.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Steuerelementklasse registriert wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Dadurch kann das Steuerelement von Containern verwendet werden, die OLE-Control-bekannt sind. `AfxOleRegisterControlClass`aktualisiert die Registrierung mit dem Namen und Speicherort des Steuerelements auf dem System und legt auch das Threadingmodell fest, das das Steuerelement in der Registrierung unterstützt. Weitere Informationen finden Sie unter [Technical Note 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Apartment-Model Threading in OLE Controls" und [About Processes and Threads](/windows/win32/ProcThread/about-processes-and-threads) in the Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

Das obige `AfxOleRegisterControlClass` Beispiel zeigt, wie mit dem Flag für einfügbar und dem Flag für Apartmentmodell ORed zusammen aufgerufen wird, um den sechsten Parameter zu erstellen:

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

Das Steuerelement wird im Dialogfeld Objekt einfügen für aktivierte Container angezeigt, und es wird apartment modellfähig sein. Wohnungsmodell-fähige Steuerelemente müssen sicherstellen, dass statische Klassendaten durch Sperren geschützt sind, sodass ein Steuerelement in einer Wohnung zwar auf die statischen Daten zugreift, aber nicht vom Planer deaktiviert wird, bevor es beendet ist, und eine andere Instanz derselben Klasse mit denselben statischen Daten beginnt. Alle Zugriffe auf die statischen Daten werden von kritischem Abschnittscode umgeben.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="afxoleregisterpropertypageclass"></a><a name="afxoleregisterpropertypageclass"></a>AfxOleRegisterPropertyPageClass

Registriert die Eigenschaftenseitenklasse bei der Windows-Registrierungsdatenbank.

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>Parameter

*hInstance*<br/>
Das Instanzhandle des Moduls, das der Eigenschaftenseitenklasse zugeordnet ist.

*clsid*<br/>
Die eindeutige Klassen-ID der Eigenschaftenseite.

*idTypeName*<br/>
Die Ressourcen-ID der Zeichenfolge, die einen vom Benutzer lesbaren Namen für die Eigenschaftenseite enthält.

*nRegFlags*<br/>
Kann die Flagge enthalten:

- `afxRegApartmentThreading`Legt das Threadingmodell in der Registrierung auf ThreadingModel = Apartment fest.

> [!NOTE]
> In MFC-Versionen vor MFC 4.2 war der Parameter **int** *nRegFlags* nicht verfügbar. Beachten Sie `afxRegInsertable` auch, dass das Flag keine gültige Option für Eigenschaftenseiten ist und einen ASSERT in MFC verursacht, wenn es festgelegt ist.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Steuerelementklasse registriert wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Dadurch kann die Eigenschaftenseite von Containern verwendet werden, die OLE-Control-erfahren sind. `AfxOleRegisterPropertyPageClass`aktualisiert die Registrierung mit dem Eigenschaftenseitennamen und ihrem Speicherort auf dem System und legt auch das Threadingmodell fest, das das Steuerelement in der Registrierung unterstützt. Weitere Informationen finden Sie unter [Technical Note 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Apartment-Model Threading in OLE Controls" und [About Processes and Threads](/windows/win32/ProcThread/about-processes-and-threads) in the Windows SDK.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="afxoleregistertypelib"></a><a name="afxoleregistertypelib"></a>AfxOleRegisterTypeLib

Registriert die Typbibliothek bei der Windows-Registrierungsdatenbank und ermöglicht die Verwendung der Typbibliothek durch andere Container, die OLE-gesteuert sind.

```
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,
    REFGUID tlid,
    LPCTSTR pszFileName = NULL,
    LPCTSTR pszHelpDir  = NULL);
```

### <a name="parameters"></a>Parameter

*hInstance*<br/>
Das Instanzhandle der Anwendung, die der Typbibliothek zugeordnet ist.

*tlid*<br/>
Die eindeutige ID der Typbibliothek.

*pszFileName*<br/>
Zeigt auf den optionalen Dateinamen einer lokalisierten Typbibliothek (. TLB)-Datei für das Steuerelement.

*pszHelpDir*<br/>
Der Name des Verzeichnisses, in dem sich die Hilfedatei für die Typbibliothek befindet. Wenn NULL, wird angenommen, dass sich die Hilfedatei im selben Verzeichnis wie die Typbibliothek selbst befindet.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Typbibliothek registriert wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion aktualisiert die Registrierung mit dem Typbibliotheksnamen und ihrem Speicherort auf dem System.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="afxoleunregisterclass"></a><a name="afxoleunregisterclass"></a>AfxOleUnregisterClass

Entfernt den Steuerelement- oder Eigenschaftenseitenklasseneintrag aus der Windows-Registrierungsdatenbank.

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>Parameter

*Clsid*<br/>
Die eindeutige Klassen-ID des Steuerelements oder der Eigenschaftenseite.

*pszProgID*<br/>
Die eindeutige Programm-ID der Steuerelement- oder Eigenschaftenseite.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Steuerelement- oder Eigenschaftenseitenklasse erfolgreich abgemeldet wurde; andernfalls 0.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="afxoleunregistertypelib"></a><a name="afxoleunregistertypelib"></a>AfxOleUnregisterTypeLib

Rufen Sie diese Funktion auf, um den Typbibliothekseintrag aus der Windows-Registrierungsdatenbank zu entfernen.

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>Parameter

*tlID*<br/>
Die eindeutige ID der Typbibliothek.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Typbibliothek erfolgreich abgemeldet wurde; andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
