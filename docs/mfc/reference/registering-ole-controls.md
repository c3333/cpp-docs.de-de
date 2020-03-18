---
title: Registrieren des OLE-Steuerelements
ms.date: 11/04/2016
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 9fcbc002913cc6cce86276796a371231ef0f32e1
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426198"
---
# <a name="registering-ole-controls"></a>Registrieren des OLE-Steuerelements

Auf OLE-Steuerelemente kann wie andere OLE-Server-Objekte von anderen OLE-fähigen Anwendungen zugegriffen werden. Dies wird erreicht, indem die Typbibliothek und die Klasse des Steuer Elements registriert werden.

Mit den folgenden Funktionen können Sie die-Klasse, die Eigenschaften Seiten und die Typbibliothek des-Steuer Elements in der Windows-Registrierungsdatenbank hinzufügen und entfernen:

### <a name="registering-ole-controls"></a>Registrieren des OLE-Steuerelements

|||
|-|-|
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|Fügt der Registrierungsdatenbank die Klasse des Steuer Elements hinzu.|
|[Afxoleregisterpropertypageclass](#afxoleregisterpropertypageclass)|Fügt der Registrierungsdatenbank eine Eigenschaften Seite des-Steuer Elements hinzu.|
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|Fügt der Registrierungsdatenbank die Typbibliothek des-Steuer Elements hinzu.|
|[Afxoleunregisterclass](#afxoleunregisterclass)|Entfernt eine Steuerelement Klasse oder eine Eigenschaften Seiten Klasse aus der Registrierungsdatenbank.|
|[Afxoleunregistertypelib](#afxoleunregistertypelib)|Entfernt die Typbibliothek des Steuer Elements aus der Registrierungsdatenbank.|

`AfxOleRegisterTypeLib` wird in der Regel in der Implementierung von `DllRegisterServer`der Steuerelement-DLL aufgerufen. Auf ähnliche Weise wird `AfxOleUnregisterTypeLib` von `DllUnregisterServer`aufgerufen. `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`und `AfxOleUnregisterClass` werden üblicherweise von der `UpdateRegistry` Member-Funktion der Klassenfactory oder Eigenschaften Seite eines Steuer Elements aufgerufen.

##  <a name="afxoleregistercontrolclass"></a>AfxOleRegisterControlClass

Registriert die Steuerelement Klasse bei der Windows-Registrierungsdatenbank.

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

*HINSTANCE*<br/>
Der Instanzhandle des Moduls, das der Steuerelement Klasse zugeordnet ist.

*CLSID*<br/>
Die eindeutige Klassen-ID des Steuer Elements.

*pszprogid*<br/>
Die eindeutige Programm-ID des Steuer Elements.

*idtyname*<br/>
Die Ressourcen-ID der Zeichenfolge, die einen vom Benutzer lesbaren Typnamen für das Steuerelement enthält.

*idbitmap*<br/>
Die Ressourcen-ID der Bitmap, die zum Darstellen des OLE-Steuer Elements in einer Symbolleiste oder Palette verwendet wird.

*nregflags*<br/>
Enthält mindestens eines der folgenden Flags:

- mit `afxRegInsertable` kann das Steuerelement im Dialogfeld Objekt einfügen für OLE-Objekte angezeigt werden.

- `afxRegApartmentThreading` legt das Threading Modell in der Registrierung auf ThreadingModel = Apartment fest.

- `afxRegFreeThreading` legt das Threading Modell in der Registrierung auf ThreadingModel = Free fest.

   Sie können die beiden Flags `afxRegApartmentThreading` und `afxRegFreeThreading` kombinieren, um ThreadingModel = both festzulegen. Weitere Informationen zur Threading Modell Registrierung finden Sie unter [InProcServer32](/windows/win32/com/inprocserver32) im Windows SDK.

> [!NOTE]
>  In MFC-Versionen vor MFC 4,2 war der **int** *nregflags* -Parameter ein boolescher Parameter ( *binsertable*), der das Einfügen des Steuer Elements aus dem Dialogfeld "Objekt einfügen" gestattet oder verweigert hat.

*dwfehlstatus*<br/>
Enthält mindestens eines der folgenden Statusflags (eine Beschreibung der Flags finden Sie unter OLEMISC-Enumeration im Windows SDK):

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
Die eindeutige ID der Steuerelement Klasse.

*wvermajor*<br/>
Die Hauptversionsnummer der Steuerelement Klasse.

*wverminor*<br/>
Die neben Versionsnummer der Steuerelement Klasse.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Steuerelement Klasse registriert wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Dadurch kann das Steuerelement von Containern verwendet werden, die OLE-Steuerelemente unterstützen. `AfxOleRegisterControlClass` aktualisiert die Registrierung mit dem Namen und Speicherort des Steuer Elements auf dem System und legt außerdem das Thread Modell fest, das das Steuerelement in der Registrierung unterstützt. Weitere Informationen finden Sie im [technischen Hinweis 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Apartment Modell Threading in OLE-Steuerelementen" und Informationen [zu Prozessen und Threads](/windows/win32/ProcThread/about-processes-and-threads) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

Im obigen Beispiel wird veranschaulicht, wie `AfxOleRegisterControlClass` mit dem-Flag für einfügbar und dem-Flag für das Apartment Modell ORed zum Erstellen des sechsten Parameters aufgerufen wird:

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

Das Steuerelement wird im Dialogfeld Objekt einfügen für aktivierte Container angezeigt, und es ist Apartment Modell fähig. Die Steuerelemente für das Apartment Modell müssen sicherstellen, dass statische Klassen Daten durch Sperren geschützt werden, sodass ein Steuerelement in einem Apartment, das auf die statischen Daten zugreift, nicht vom Scheduler deaktiviert wird, bevor es abgeschlossen wird, und eine andere Instanz derselben Klasse beginnt mit der Verwendung von die gleichen statischen Daten. Alle Zugriffe auf die statischen Daten werden durch den kritischen Abschnitts Code umgeben.

### <a name="requirements"></a>Voraussetzungen

  **Header** afxctl. h

##  <a name="afxoleregisterpropertypageclass"></a>Afxoleregisterpropertypageclass

Registriert die Eigenschaften Seiten Klasse bei der Windows-Registrierungsdatenbank.

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>Parameter

*HINSTANCE*<br/>
Der Instanzhandle des Moduls, das der Eigenschaften Seiten Klasse zugeordnet ist.

*CLSID*<br/>
Die eindeutige Klassen-ID der Eigenschaften Seite.

*idtyname*<br/>
Die Ressourcen-ID der Zeichenfolge, die einen vom Benutzer lesbaren Namen für die Eigenschaften Seite enthält.

*nregflags*<br/>
Kann das-Flag enthalten:

- `afxRegApartmentThreading` legt das Threading Modell in der Registrierung auf ThreadingModel = Apartment fest.

> [!NOTE]
>  In MFC-Versionen vor MFC 4,2 war der **int** *nregflags* -Parameter nicht verfügbar. Beachten Sie auch, dass das `afxRegInsertable`-Flag keine gültige Option für Eigenschaften Seiten ist und eine Bestätigung in MFC verursacht, wenn es festgelegt ist.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Steuerelement Klasse registriert wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Dadurch kann die Eigenschaften Seite von Containern verwendet werden, die OLE-Steuerelemente unterstützen. `AfxOleRegisterPropertyPageClass` aktualisiert die Registrierung mit dem Namen der Eigenschaften Seite und deren Speicherort auf dem System und legt außerdem das Thread Modell fest, das das Steuerelement in der Registrierung unterstützt. Weitere Informationen finden Sie im [technischen Hinweis 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Apartment Modell Threading in OLE-Steuerelementen" und Informationen [zu Prozessen und Threads](/windows/win32/ProcThread/about-processes-and-threads) in der Windows SDK.

### <a name="requirements"></a>Voraussetzungen

  **Header** afxctl. h

##  <a name="afxoleregistertypelib"></a>AfxOleRegisterTypeLib

Registriert die Typbibliothek bei der Windows-Registrierungsdatenbank und ermöglicht die Verwendung der Typbibliothek durch andere Container, die die OLE-Kontrolle unterstützen.

```
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,
    REFGUID tlid,
    LPCTSTR pszFileName = NULL,
    LPCTSTR pszHelpDir  = NULL);
```

### <a name="parameters"></a>Parameter

*HINSTANCE*<br/>
Der Instanzhandle der Anwendung, die der Typbibliothek zugeordnet ist.

*tlid*<br/>
Die eindeutige ID der Typbibliothek.

*pszFileName*<br/>
Verweist auf den optionalen Dateinamen einer lokalisierten Typbibliothek (. TLB-Datei für das Steuerelement.

*pszhelpdir*<br/>
Der Name des Verzeichnisses, in dem sich die Hilfedatei für die Typbibliothek befindet. Wenn der Wert NULL ist, wird davon ausgegangen, dass sich die Hilfedatei im selben Verzeichnis wie die Typbibliothek selbst befindet.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Typbibliothek registriert wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Funktion aktualisiert die Registrierung mit dem Namen der Typbibliothek und deren Speicherort auf dem System.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>Voraussetzungen

  **Header** afxdisp. h

##  <a name="afxoleunregisterclass"></a>Afxoleunregisterclass

Entfernt das Steuerelement oder den Klassen Eintrag der Eigenschaften Seite aus der Windows-Registrierungsdatenbank.

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>Parameter

*clsID*<br/>
Die eindeutige Klassen-ID des Steuer Elements oder der Eigenschaften Seite.

*pszprogid*<br/>
Die eindeutige Programm-ID des Steuer Elements oder der Eigenschaften Seite.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die Registrierung für das Steuerelement oder die Eigenschaften Seiten Klasse erfolgreich aufgehoben wurde. andernfalls 0.

### <a name="requirements"></a>Voraussetzungen

  **Header** afxctl. h

##  <a name="afxoleunregistertypelib"></a>Afxoleunregistertypelib

Mit dieser Funktion können Sie den Typbibliotheks Eintrag aus der Windows-Registrierungsdatenbank entfernen.

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>Parameter

*tlid*<br/>
Die eindeutige ID der Typbibliothek.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die Registrierung der Typbibliothek erfolgreich aufgehoben wurde. andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>Voraussetzungen

  **Header** afxdisp. h

## <a name="see-also"></a>Siehe auch

[Makros und Globals](../../mfc/reference/mfc-macros-and-globals.md)
