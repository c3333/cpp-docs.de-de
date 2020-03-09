---
title: COleObjectFactory-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleObjectFactory
- AFXDISP/COleObjectFactory
- AFXDISP/COleObjectFactory::COleObjectFactory
- AFXDISP/COleObjectFactory::GetClassID
- AFXDISP/COleObjectFactory::IsLicenseValid
- AFXDISP/COleObjectFactory::IsRegistered
- AFXDISP/COleObjectFactory::Register
- AFXDISP/COleObjectFactory::RegisterAll
- AFXDISP/COleObjectFactory::Revoke
- AFXDISP/COleObjectFactory::RevokeAll
- AFXDISP/COleObjectFactory::UnregisterAll
- AFXDISP/COleObjectFactory::UpdateRegistry
- AFXDISP/COleObjectFactory::UpdateRegistryAll
- AFXDISP/COleObjectFactory::GetLicenseKey
- AFXDISP/COleObjectFactory::OnCreateObject
- AFXDISP/COleObjectFactory::VerifyLicenseKey
- AFXDISP/COleObjectFactory::VerifyUserLicense
helpviewer_keywords:
- COleObjectFactory [MFC], COleObjectFactory
- COleObjectFactory [MFC], GetClassID
- COleObjectFactory [MFC], IsLicenseValid
- COleObjectFactory [MFC], IsRegistered
- COleObjectFactory [MFC], Register
- COleObjectFactory [MFC], RegisterAll
- COleObjectFactory [MFC], Revoke
- COleObjectFactory [MFC], RevokeAll
- COleObjectFactory [MFC], UnregisterAll
- COleObjectFactory [MFC], UpdateRegistry
- COleObjectFactory [MFC], UpdateRegistryAll
- COleObjectFactory [MFC], GetLicenseKey
- COleObjectFactory [MFC], OnCreateObject
- COleObjectFactory [MFC], VerifyLicenseKey
- COleObjectFactory [MFC], VerifyUserLicense
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
ms.openlocfilehash: 22805550d13ecb400b151495363e5eda2dfb3b76
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856975"
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory-Klasse

Implementiert die OLE-Klassenfactory, die OLE-Objekte wie Server, Automatisierungsobjekte und Dokumente erstellt.

## <a name="syntax"></a>Syntax

```
class COleObjectFactory : public CCmdTarget
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[COleObjectFactory:: COleObjectFactory](#coleobjectfactory)|Erstellt ein `COleObjectFactory`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[COleObjectFactory:: GetClassID](#getclassid)|Gibt die OLE-Klassen-ID der Objekte zurück, die von dieser Factory erstellt werden.|
|[COleObjectFactory:: islicensevalid](#islicensevalid)|Bestimmt, ob die Lizenz für das Steuerelement gültig ist.|
|[COleObjectFactory:: IsRegistered](#isregistered)|Gibt an, ob die Objektfactory bei den OLE-System-DLLs registriert ist.|
|[COleObjectFactory:: Register](#register)|Registriert diese Objektfactory bei den OLE-System-DLLs.|
|[COleObjectFactory:: RegisterAll](#registerall)|Registriert alle objektfactorys der Anwendung bei OLE-System-DLLs.|
|[COleObjectFactory:: Widerruf](#revoke)|Widerruft die Registrierung dieser Objektfactory bei den OLE-System-DLLs.|
|[COleObjectFactory:: RevokeAll](#revokeall)|Widerruft die Registrierungen der objektfactorys einer Anwendung mit den OLE-System-DLLs.|
|[COleObjectFactory:: UnregisterAll](#unregisterall)|Hebt die Registrierung aller objektfactorys einer Anwendung auf.|
|[COleObjectFactory:: UpdateRegistry](#updateregistry)|Registriert diese Objektfactory bei der OLE-Systemregistrierung.|
|[COleObjectFactory:: UpdateRegistryAll](#updateregistryall)|Registriert alle objektfactorys der Anwendung bei der OLE-Systemregistrierung.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|Beschreibung|
|----------|-----------------|
|[COleObjectFactory:: getlicenlkey](#getlicensekey)|Fordert einen eindeutigen Schlüssel aus der DLL des-Steuer Elements an.|
|[COleObjectFactory:: onkreateobject](#oncreateobject)|Wird von Framework aufgerufen, um ein neues Objekt des Typs dieser Factory zu erstellen.|
|[COleObjectFactory:: verifylicenlkey](#verifylicensekey)|Überprüft, ob der im-Steuerelement eingebettete Schlüssel mit dem im Container eingebetteten Schlüssel übereinstimmt.|
|[COleObjectFactory:: verilyuserlicense](#verifyuserlicense)|Überprüft, ob das Steuerelement für die Entwurfszeit Verwendung lizenziert ist.|

## <a name="remarks"></a>Hinweise

Die `COleObjectFactory`-Klasse verfügt über Element Funktionen zum Ausführen der folgenden Funktionen:

- Verwalten der Registrierung von Objekten.

- Aktualisieren des OLE-System Registers sowie der Lauf Zeit Registrierung, bei der OLE darüber informiert wird, dass Objekte ausgeführt werden und bereit sind, Nachrichten zu empfangen.

- Erzwingen der Lizenzierung durch Einschränken der Verwendung des Steuer Elements auf lizenzierte Entwickler zur Entwurfszeit und auf lizenzierte Anwendungen zur Laufzeit.

- Registrieren von steuerungsobjefactorys bei der OLE-Systemregistrierung

Weitere Informationen zur Objekt Erstellung finden Sie in den Artikeln [Datenobjekte und Datenquellen (OLE)](../../mfc/data-objects-and-data-sources-ole.md) und [Datenobjekte und Datenquellen: Erstellung und Zerstörung](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Weitere Informationen zur Registrierung finden Sie im Artikel [Registrierung](../../mfc/registration.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxdisp.h

##  <a name="coleobjectfactory"></a>COleObjectFactory:: COleObjectFactory

Erstellt ein `COleObjectFactory` Objekt, initialisiert es als nicht registrierte Objektfactory und fügt es der Liste der Factorys hinzu.

```
COleObjectFactory(
    REFCLSID clsid,
    CRuntimeClass* pRuntimeClass,
    BOOL bMultiInstance,
    LPCTSTR lpszProgID);

COleObjectFactory(
    REFCLSID clsid,
    CRuntimeClass* pRuntimeClass,
    BOOL bMultiInstance,
    int nFlags,
    LPCTSTR lpszProgID);
```

### <a name="parameters"></a>Parameter

*CLSID*<br/>
Verweis auf die OLE-Klassen-ID, die diese Objektfactory darstellt.

*pruntimeclass*<br/>
Ein Zeiger auf die Lauf Zeit Klasse der Objekte C++ , die diese Factory erstellen kann.

*Parameter bmultiinstance*<br/>
Gibt an, ob eine einzelne Instanz der Anwendung mehrere Instanziierungen unterstützen kann. TRUE gibt an, dass für jede Anforderung zum Erstellen eines Objekts mehrere Instanzen der Anwendung gestartet werden.

*nFlags*<br/>
Enthält mindestens eines der folgenden Flags:

- `afxRegDefault` legt das Threading Modell auf ThreadingModel = Apartment fest.

- mit `afxRegInsertable` kann das Steuerelement im Dialogfeld **Objekt einfügen** für OLE-Objekte angezeigt werden.

- `afxRegApartmentThreading` legt das Threading Modell in der Registrierung auf ThreadingModel = Apartment fest.

- `afxRegFreeThreading` legt das Threading Modell in der Registrierung auf ThreadingModel = Free fest.

   Sie können die beiden Flags `afxRegApartmentThreading` und `afxRegFreeThreading` kombinieren, um ThreadingModel = both festzulegen. Weitere Informationen zur Threading Modell Registrierung finden Sie unter [InProcServer32](/windows/win32/com/inprocserver32) im Windows SDK.

*lpszprogid*<br/>
Zeiger auf eine Zeichenfolge, die eine verbale Programm Kennung enthält, z. b. "Microsoft Excel".

### <a name="remarks"></a>Hinweise

Um das-Objekt zu verwenden, müssen Sie es jedoch registrieren.

Weitere Informationen finden Sie unter [CLSID-Schlüssel](/windows/win32/com/clsid-key-hklm) in der Windows SDK.

##  <a name="getclassid"></a>COleObjectFactory:: GetClassID

Gibt einen Verweis auf die OLE-Klassen-ID zurück, die diese Factory darstellt.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Rückgabewert

Verweis auf die OLE-Klassen-ID, die diese Factory darstellt.

### <a name="remarks"></a>Hinweise

Weitere Informationen finden Sie unter [CLSID-Schlüssel](/windows/win32/com/clsid-key-hklm) in der Windows SDK.

##  <a name="getlicensekey"></a>COleObjectFactory:: getlicenlkey

Fordert einen eindeutigen Lizenzschlüssel aus der DLL des-Steuer Elements an und speichert ihn im BSTR, auf den *pbstrinkey*zeigt.

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>Parameter

*dwReserved*<br/>
Für zukünftige Verwendung reserviert.

*pbstraukey*<br/>
Zeiger auf einen BSTR-Wert, der den Lizenzschlüssel speichert.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Lizenzschlüssel Zeichenfolge nicht NULL ist. andernfalls 0.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung dieser Funktion gibt 0 zurück und speichert nichts in BSTR. Wenn Sie das Projekt mithilfe von MFC ActiveX controlwizard erstellen, liefert controlwizard eine außer Kraft setzung, mit der der Lizenzschlüssel des Steuer Elements abgerufen wird.

##  <a name="islicensevalid"></a>COleObjectFactory:: islicensevalid

Bestimmt, ob die Lizenz für das Steuerelement gültig ist.

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich; andernfalls false.

##  <a name="isregistered"></a>COleObjectFactory:: IsRegistered

Gibt einen Wert ungleich 0 (null) zurück, wenn die Factory bei den OLE-System-DLLs registriert ist.

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Factory registriert ist. andernfalls 0.

##  <a name="oncreateobject"></a>COleObjectFactory:: onkreateobject

Wird von Framework aufgerufen, um ein neues-Objekt zu erstellen.

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das erstellte-Objekt. Wenn ein Fehler auftritt, kann eine Speicher Ausnahme ausgelöst werden.

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese Funktion, um das Objekt aus einem anderen Element als der [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) zu erstellen, die an den Konstruktor übergeben wird.

##  <a name="register"></a>COleObjectFactory:: Register

Registriert diese Objektfactory bei den OLE-System-DLLs.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Factory erfolgreich registriert wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Funktion wird in der Regel von [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) aufgerufen, wenn die Anwendung gestartet wird.

##  <a name="registerall"></a>COleObjectFactory:: RegisterAll

Registriert alle objektfactorys der Anwendung mit den OLE-System-DLLs.

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die Factorys erfolgreich registriert wurden. andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Funktion wird in der Regel von [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) aufgerufen, wenn die Anwendung gestartet wird.

##  <a name="revoke"></a>COleObjectFactory:: Widerruf

Widerruft die Registrierung dieser Objektfactory bei den OLE-System-DLLs.

```
void Revoke();
```

### <a name="remarks"></a>Hinweise

Das Framework ruft diese Funktion automatisch auf, bevor die Anwendung beendet wird. Wenn erforderlich, nennen Sie es von einer außer Kraft Setzung von [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="revokeall"></a>COleObjectFactory:: RevokeAll

Widerruft die Registrierungen aller objektfactorys der Anwendung mit den OLE-System-DLLs.

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>Hinweise

Das Framework ruft diese Funktion automatisch auf, bevor die Anwendung beendet wird. Wenn erforderlich, nennen Sie es von einer außer Kraft Setzung von [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="unregisterall"></a>COleObjectFactory:: UnregisterAll

Hebt die Registrierung aller objektfactorys einer Anwendung auf.

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich; andernfalls FALSE.

##  <a name="updateregistry"></a>COleObjectFactory:: UpdateRegistry

Registriert alle objektfactorys der Anwendung bei der OLE-Systemregistrierung.

```
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>Parameter

*lpszprogid*<br/>
Zeiger auf eine Zeichenfolge, die den lesbaren Programm Bezeichner enthält, z. b. "Excel. Document. 5".

*bregister*<br/>
Bestimmt, ob die Objektfactory der Steuerelement Klasse registriert werden soll.

### <a name="remarks"></a>Hinweise

Im folgenden finden Sie eine kurze Erörterung der beiden Formen für diese Funktion:

- **UpdateRegistry (** `lpszProgID` **)** Registriert diese Objektfactory bei der OLE-Systemregistrierung. Diese Funktion wird in der Regel von [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) aufgerufen, wenn die Anwendung gestartet wird.

- **UpdateRegistry (** `bRegister` **)** Diese Form der-Funktion ist über schreibbar. Wenn *bregister* den Wert true hat, registriert diese Funktion die Steuerelement Klasse bei der Systemregistrierung. Andernfalls wird die Registrierung der-Klasse aufgehoben.

   Wenn Sie den MFC-ActiveX-controlwizard zum Erstellen des Projekts verwenden, stellt controlwizard eine außer Kraft setzung für diese reine virtuelle Funktion bereit.

##  <a name="updateregistryall"></a>COleObjectFactory:: UpdateRegistryAll

Registriert alle objektfactorys der Anwendung bei der OLE-Systemregistrierung.

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parameter

*bregister*<br/>
Bestimmt, ob die Objektfactory der Steuerelement Klasse registriert werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die Factorys erfolgreich aktualisiert wurden. andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Funktion wird in der Regel von [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) aufgerufen, wenn die Anwendung gestartet wird.

##  <a name="verifylicensekey"></a>COleObjectFactory:: verifylicenlkey

Überprüft, ob der Container für die Verwendung des OLE-Steuer Elements lizenziert ist.

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>Parameter

*bstrinkey*<br/>
Ein BSTR, das die Version der Lizenz Zeichenfolge des Containers speichert.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Laufzeitlizenz gültig ist. andernfalls 0.

### <a name="remarks"></a>Hinweise

Die Standardversion ruft [getlicenskey](#getlicensekey) auf, um eine Kopie der Lizenz Zeichenfolge des Steuer Elements zu erhalten, und vergleicht sie mit der Zeichenfolge in *bstrinkey*. Wenn die beiden Zeichen folgen Stimmen, gibt die Funktion einen Wert ungleich 0 (null) zurück. Andernfalls wird 0 zurückgegeben.

Sie können diese Funktion überschreiben, um eine angepasste Überprüfung der Lizenz bereitzustellen.

Die Funktion [VerifyUserLicense](#verifyuserlicense) überprüft die Entwurfszeit Lizenz.

##  <a name="verifyuserlicense"></a>COleObjectFactory:: verilyuserlicense

Überprüft die Entwurfszeit Lizenz für das OLE-Steuerelement.

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Entwurfszeit Lizenz gültig ist. andernfalls 0.

## <a name="see-also"></a>Siehe auch

[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleTemplateServer-Klasse](../../mfc/reference/coletemplateserver-class.md)
