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
ms.openlocfilehash: 9f3d86cf735c02b6021441c66d9fd64547f6d6c2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374910"
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory-Klasse

Implementiert die OLE-Klassenfactory, die OLE-Objekte wie Server, Automatisierungsobjekte und Dokumente erstellt.

## <a name="syntax"></a>Syntax

```
class COleObjectFactory : public CCmdTarget
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleObjectFactory::COleObjectFactory](#coleobjectfactory)|Erstellt ein `COleObjectFactory`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleObjectFactory::GetClassID](#getclassid)|Gibt die OLE-Klassen-ID der Objekte zurück, die diese Factory erstellt.|
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|Bestimmt, ob die Lizenz des Steuerelements gültig ist.|
|[COleObjectFactory::IsRegistered](#isregistered)|Gibt an, ob die Objektfactory bei den OLE-System-DLLs registriert ist.|
|[COleObjectFactory::Registrieren](#register)|Registriert diese Objektfactory bei den OLE-System-DLLs.|
|[COleObjectFactory::RegisterAll](#registerall)|Registriert alle Objektfactorys der Anwendung mit OLE-System-DLLs.|
|[COleObjectFactory::Revoke](#revoke)|Widerruft die Registrierung dieses Objektwerks bei den OLE-System-DLLs.|
|[COleObjectFactory::RevokeAll](#revokeall)|Widerruft die Registrierungen der Objektfabriken einer Anwendung mit den OLE-System-DLLs.|
|[COleObjectFactory::UnregisterAll](#unregisterall)|Entregistriert alle Objektfabriken einer Anwendung.|
|[COleObjectFactory::UpdateRegistry](#updateregistry)|Registriert diese Objektfactory bei der OLE-Systemregistrierung.|
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|Registriert alle Objektfactorys der Anwendung in der OLE-Systemregistrierung.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|Fordert einen eindeutigen Schlüssel aus der DLL des Steuerelements an.|
|[COleObjectFactory::OnCreateObject](#oncreateobject)|Wird vom Framework aufgerufen, um ein neues Objekt vom Typ dieser Factory zu erstellen.|
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|Überprüft, ob der im Steuerelement eingebettete Schlüssel mit dem im Container eingebetteten Schlüssel übereinstimmt.|
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|Überprüft, ob das Steuerelement für die Entwurfszeitverwendeter lizenziert ist.|

## <a name="remarks"></a>Bemerkungen

Die `COleObjectFactory` Klasse verfügt über Memberfunktionen zum Ausführen der folgenden Funktionen:

- Verwalten der Registrierung von Objekten.

- Aktualisieren des OLE-Systemregisters sowie der Laufzeitregistrierung, die OLE darüber informiert, dass Objekte ausgeführt werden und zum Empfangen von Nachrichten bereit sind.

- Erzwingen der Lizenzierung durch Beschränkung der Verwendung des Steuerelements auf lizenzierte Entwickler zur Entwurfszeit und auf lizenzierte Anwendungen zur Laufzeit.

- Registrieren von Steuerobjektfactorys bei der OLE-Systemregistrierung.

Weitere Informationen zur Objekterstellung finden Sie in den Artikeln [Data Objects and Data Sources (OLE)](../../mfc/data-objects-and-data-sources-ole.md) und Data Objects and Data [Sources: Creation and Destruction](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Weitere Informationen zur Registrierung finden Sie im Artikel [Registrierung](../../mfc/registration.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="coleobjectfactorycoleobjectfactory"></a><a name="coleobjectfactory"></a>COleObjectFactory::COleObjectFactory

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

*clsid*<br/>
Verweis auf die OLE-Klassen-ID, die diese Objektfactory darstellt.

*pRuntimeClass*<br/>
Zeiger auf die Laufzeitklasse der C++-Objekte, die diese Factory erstellen kann.

*bMultiInstance*<br/>
Gibt an, ob eine einzelne Instanz der Anwendung mehrere Instanziierungen unterstützen kann. Wenn TRUE, werden mehrere Instanzen der Anwendung für jede Anforderung zum Erstellen eines Objekts gestartet.

*nFlags*<br/>
Enthält eines oder mehrere der folgenden Flags:

- `afxRegDefault`Legt das Threadingmodell auf ThreadingModel=Apartment fest.

- `afxRegInsertable`Lässt das Steuerelement im Dialogfeld **Objekt** einfügen für OLE-Objekte angezeigt werden.

- `afxRegApartmentThreading`Legt das Threadingmodell in der Registrierung auf ThreadingModel=Apartment fest.

- `afxRegFreeThreading`Legt das Threadingmodell in der Registrierung auf ThreadingModel=Free fest.

   Sie können die `afxRegApartmentThreading` beiden `afxRegFreeThreading` Flags kombinieren und ThreadingModel=Both festlegen. Weitere Informationen zur Threadingmodellregistrierung finden Sie unter [InprocServer32](/windows/win32/com/inprocserver32) im Windows SDK.

*lpszProgID*<br/>
Zeiger auf eine Zeichenfolge, die einen verbalen Programmbezeichner enthält, z. B. "Microsoft Excel".

### <a name="remarks"></a>Bemerkungen

Um das Objekt zu verwenden, müssen Sie es jedoch registrieren.

Weitere Informationen finden Sie unter [CLSID-Schlüssel](/windows/win32/com/clsid-key-hklm) im Windows SDK.

## <a name="coleobjectfactorygetclassid"></a><a name="getclassid"></a>COleObjectFactory::GetClassID

Gibt einen Verweis auf die OLE-Klassen-ID zurück, die diese Factory darstellt.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Rückgabewert

Verweis auf die OLE-Klassen-ID, die diese Factory darstellt.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [CLSID-Schlüssel](/windows/win32/com/clsid-key-hklm) im Windows SDK.

## <a name="coleobjectfactorygetlicensekey"></a><a name="getlicensekey"></a>COleObjectFactory::GetLicenseKey

Fordert einen eindeutigen Lizenzschlüssel aus der DLL des Steuerelements an und speichert ihn im BSTR, auf den von *pbstrKey*verwiesen wird.

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>Parameter

*dwReserved*<br/>
Für die zukünftige Verwendung reserviert.

*pbstrKey*<br/>
Zeigen Sie auf einen BSTR, in dem der Lizenzschlüssel gespeichert wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Lizenzschlüsselzeichenfolge nicht NULL ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Funktion gibt 0 zurück und speichert nichts im BSTR. Wenn Sie MFC ActiveX ControlWizard zum Erstellen Ihres Projekts verwenden, stellt ControlWizard eine Außerkraftsetzung bereit, die den Lizenzschlüssel des Steuerelements abruft.

## <a name="coleobjectfactoryislicensevalid"></a><a name="islicensevalid"></a>COleObjectFactory::IsLicenseValid

Bestimmt, ob die Lizenz des Steuerelements gültig ist.

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolguli; ansonsten falsch.

## <a name="coleobjectfactoryisregistered"></a><a name="isregistered"></a>COleObjectFactory::IsRegistered

Gibt einen Wert ungleich Null zurück, wenn die Factory bei den OLE-System-DLLs registriert ist.

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Fabrik registriert ist; andernfalls 0.

## <a name="coleobjectfactoryoncreateobject"></a><a name="oncreateobject"></a>COleObjectFactory::OnCreateObject

Wird vom Framework aufgerufen, um ein neues Objekt zu erstellen.

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das erstellte Objekt. Es kann eine Speicherausnahme auslösen, wenn sie fehlschlägt.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um das Objekt aus etwas anderem als der [Anlaufzeitclass](../../mfc/reference/cruntimeclass-structure.md) zu erstellen, die an den Konstruktor übergeben wird.

## <a name="coleobjectfactoryregister"></a><a name="register"></a>COleObjectFactory::Registrieren

Registriert diese Objektfactory bei den OLE-System-DLLs.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Factory erfolgreich registriert wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird normalerweise von [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) aufgerufen, wenn die Anwendung gestartet wird.

## <a name="coleobjectfactoryregisterall"></a><a name="registerall"></a>COleObjectFactory::RegisterAll

Registriert alle Objektfactorys der Anwendung mit den OLE-System-DLLs.

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Fabriken erfolgreich registriert sind; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird normalerweise von [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) aufgerufen, wenn die Anwendung gestartet wird.

## <a name="coleobjectfactoryrevoke"></a><a name="revoke"></a>COleObjectFactory::Revoke

Widerruft die Registrierung dieses Objektwerks bei den OLE-System-DLLs.

```
void Revoke();
```

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Funktion automatisch auf, bevor die Anwendung beendet wird. Rufen Sie es bei Bedarf über eine Außerkraftsetzung von [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)auf.

## <a name="coleobjectfactoryrevokeall"></a><a name="revokeall"></a>COleObjectFactory::RevokeAll

Widerruft alle Registrierungen der Objektfabriken der Anwendung mit den OLE-System-DLLs.

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Funktion automatisch auf, bevor die Anwendung beendet wird. Rufen Sie es bei Bedarf über eine Außerkraftsetzung von [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)auf.

## <a name="coleobjectfactoryunregisterall"></a><a name="unregisterall"></a>COleObjectFactory::UnregisterAll

Entregistriert alle Objektfabriken einer Anwendung.

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

## <a name="coleobjectfactoryupdateregistry"></a><a name="updateregistry"></a>COleObjectFactory::UpdateRegistry

Registriert alle Objektfactorys der Anwendung in der OLE-Systemregistrierung.

```
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>Parameter

*lpszProgID*<br/>
Zeiger auf eine Zeichenfolge, die den vom Menschen lesbaren Programmbezeichner enthält, z. B. "Excel.Document.5."

*bRegister*<br/>
Bestimmt, ob die Objektfactory der Steuerelementklasse registriert werden soll.

### <a name="remarks"></a>Bemerkungen

Es folgen kurze Diskussionen über die beiden Formulare für diese Funktion:

- **UpdateRegistry(** `lpszProgID` **)** Registriert diese Objektfactory bei der OLE-Systemregistrierung. Diese Funktion wird normalerweise von [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) aufgerufen, wenn die Anwendung gestartet wird.

- **UpdateRegistry(** `bRegister` **)** Diese Form der Funktion ist überschreibbar. Wenn *bRegister* TRUE ist, registriert diese Funktion die Steuerklasse bei der Systemregistrierung. Andernfalls wird die Registrierung der Klasse aufheben.

   Wenn Sie MFC ActiveX ControlWizard zum Erstellen Ihres Projekts verwenden, stellt ControlWizard eine Außerkraftsetzung dieser reinen virtuellen Funktion bereit.

## <a name="coleobjectfactoryupdateregistryall"></a><a name="updateregistryall"></a>COleObjectFactory::UpdateRegistryAll

Registriert alle Objektfactorys der Anwendung in der OLE-Systemregistrierung.

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parameter

*bRegister*<br/>
Bestimmt, ob die Objektfactory der Steuerelementklasse registriert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Fabriken erfolgreich aktualisiert wurden; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird normalerweise von [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) aufgerufen, wenn die Anwendung gestartet wird.

## <a name="coleobjectfactoryverifylicensekey"></a><a name="verifylicensekey"></a>COleObjectFactory::VerifyLicenseKey

Überprüft, ob der Container für die Verwendung des OLE-Steuerelements lizenziert ist.

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>Parameter

*bstrKey*<br/>
Ein BSTR, in dem die Version des Containers der Lizenzzeichenfolge gespeichert wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Laufzeitlizenz gültig ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Standardversion ruft [GetLicenseKey](#getlicensekey) auf, um eine Kopie der Lizenzzeichenfolge des Steuerelements abzubekommen, und vergleicht sie mit der Zeichenfolge in *bstrKey*. Wenn die beiden Zeichenfolgen übereinstimmen, gibt die Funktion einen Wert ungleich Null zurück. Andernfalls wird 0 zurückgegeben.

Sie können diese Funktion überschreiben, um eine benutzerdefinierte Überprüfung der Lizenz bereitzustellen.

Die Funktion [VerifyUserLicense](#verifyuserlicense) überprüft die Entwurfszeitlizenz.

## <a name="coleobjectfactoryverifyuserlicense"></a><a name="verifyuserlicense"></a>COleObjectFactory::VerifyUserLicense

Überprüft die Entwurfszeitlizenz für das OLE-Steuerelement.

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Entwurfszeitlizenz gültig ist; andernfalls 0.

## <a name="see-also"></a>Siehe auch

[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleTemplateServer-Klasse](../../mfc/reference/coletemplateserver-class.md)
