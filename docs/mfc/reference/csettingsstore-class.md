---
title: CSettingsStore Class
ms.date: 11/04/2016
f1_keywords:
- CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::Close
- AFXSETTINGSSTORE/CSettingsStore::CreateKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteValue
- AFXSETTINGSSTORE/CSettingsStore::Open
- AFXSETTINGSSTORE/CSettingsStore::Read
- AFXSETTINGSSTORE/CSettingsStore::Write
helpviewer_keywords:
- CSettingsStore [MFC], CSettingsStore
- CSettingsStore [MFC], Close
- CSettingsStore [MFC], CreateKey
- CSettingsStore [MFC], DeleteKey
- CSettingsStore [MFC], DeleteValue
- CSettingsStore [MFC], Open
- CSettingsStore [MFC], Read
- CSettingsStore [MFC], Write
ms.assetid: 0ea181de-a13e-4b29-b560-7c43838223ff
ms.openlocfilehash: b1acf959c371aa23ac55ace7fea9466f0e20813f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318468"
---
# <a name="csettingsstore-class"></a>CSettingsStore Class

Kapselt Windows-API-Funktionen und stellt eine objektorientierte Schnittstelle für den Zugriff auf die Registrierung bereit.

## <a name="syntax"></a>Syntax

```
class CSettingsStore : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSettingsStore::CSettingsStore](#csettingsstore)|Erstellt ein `CSettingsStore`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSettingsStore::Schließen](#close)|Schließt den geöffneten Registrierungsschlüssel.|
|[CSettingsStore::CreateKey](#createkey)|Öffnet den angegebenen Schlüssel oder erstellt ihn, wenn er nicht vorhanden ist.|
|[CSettingsStore::DeleteKey](#deletekey)|Löscht den angegebenen Schlüssel und alle untergeordneten Elemente.|
|[CSettingsStore::DeleteValue](#deletevalue)|Löscht den angegebenen Wert des geöffneten Schlüssels.|
|[CSettingsStore::Öffnen](#open)|Öffnet den angegebenen Schlüssel.|
|[CSettingsStore::Lesen](#read)|Ruft die Daten für einen angegebenen Schlüsselwert ab.|
|[CSettingsStore::Schreiben](#write)|Schreibt einen Wert in die Registrierung unter dem geöffneten Schlüssel.|

## <a name="remarks"></a>Bemerkungen

Die `CreateKey` Memberfunktionen `Open` sind sehr ähnlich. Wenn der Registrierungsschlüssel `CreateKey` bereits `Open` vorhanden ist und auf die gleiche Weise funktioniert. Wenn der Registrierungsschlüssel jedoch nicht `CreateKey` vorhanden ist, wird er erstellt, während `Open` er einen Fehlerwert zurückgibt.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie die `CSettingsStore` Open- und Read-Methoden der Klasse verwendet werden. Dieser Codeausschnitt ist Teil des [Tool Tip Demo-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxsettingsstore.h

## <a name="csettingsstoreclose"></a><a name="close"></a>CSettingsStore::Schließen

Schließt den geöffneten Registrierungsschlüssel.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Standardmäßig wird diese Methode vom Destruktor der [CSettingsStore-Klasse](../../mfc/reference/csettingsstore-class.md)aufgerufen.

## <a name="csettingsstorecreatekey"></a><a name="createkey"></a>CSettingsStore::CreateKey

Öffnet einen Registrierungsschlüssel oder erstellt ihn, wenn er nicht vorhanden ist.

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>Parameter

*pszPath*<br/>
[in] Gibt den Namen eines Schlüssels an, der erstellt oder geöffnet werden soll.

### <a name="return-value"></a>Rückgabewert

0, wenn erfolgreich; andernfalls ein Wert ungleich Null.

### <a name="remarks"></a>Bemerkungen

`CreateKey`verwendet `m_hKey` als Stamm von Registrierungsanfragen. Es sucht nach *pszPath* als `m_hKey`Unterschlüssel von . Wenn der Schlüssel nicht `CreateKey` vorhanden ist, wird er erstellt. Andernfalls wird der Schlüssel geöffnet. `CreateKey`setzt `m_hKey` dann auf den erstellten oder geöffneten Schlüssel.

## <a name="csettingsstorecsettingsstore"></a><a name="csettingsstore"></a>CSettingsStore::CSettingsStore

Erstellt ein `CSettngsStore` -Objekt.

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Parameter

*bAdmin*<br/>
[in] Boolescher Parameter, der `CSettingsStore` angibt, ob das Objekt im Administratormodus wirkt.

*bReadOnly*<br/>
[in] Boolescher Parameter, der `CSettingsStore` angibt, ob das Objekt im schreibgeschützten Modus erstellt wird.

### <a name="remarks"></a>Bemerkungen

Wenn *bAdmin* auf TRUE `m_hKey` festgelegt ist, wird die Membervariable auf **HKEY_LOCAL_MACHINE**festgelegt. Wenn Sie *bAdmin* auf `m_hKey` FALSE setzen, wird **auf HKEY_CURRENT_USER**festgelegt.

Der Sicherheitszugriff hängt vom *Parameter bReadOnly* ab. Wenn *bReadonly* FALSE ist, wird der Sicherheitszugriff auf **KEY_ALL_ACCESS**festgelegt. Wenn *bReadyOnly* TRUE ist, wird der Sicherheitszugriff auf eine Kombination aus **KEY_QUERY_VALUE, KEY_NOTIFY** und **KEY_ENUMERATE_SUB_KEYS**festgelegt. Weitere Informationen zum Sicherheitszugriff zusammen mit der Registrierung finden Sie unter [Registrierungsschlüsselsicherheit und Zugriffsrechte](/windows/win32/SysInfo/registry-key-security-and-access-rights).

Der Destruktor für `CSettingsStore` automatische Freigaben. `m_hKey`

## <a name="csettingsstoredeletekey"></a><a name="deletekey"></a>CSettingsStore::DeleteKey

Löscht einen Schlüssel und alle untergeordneten Elemente aus der Registrierung.

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>Parameter

*pszPath*<br/>
[in] Der Name des zu löschenden Schlüssels.

*bAdmin*<br/>
[in] Schalter, der den Speicherort des zu löschenden Schlüssels angibt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Methode schlägt `CSettingsStore` fehl, wenn sich das Objekt im schreibgeschützten Modus befindet.

Wenn der Parameter *bAdmin* Null ist, sucht nach dem Schlüssel, `DeleteKey` der unter **HKEY_CURRENT_USER**gelöscht werden soll. Wenn *bAdmin* ungleich `DeleteKey` Null ist, sucht nach dem Schlüssel, der unter **HKEY_LOCAL_MACHINE**gelöscht werden soll.

## <a name="csettingsstoredeletevalue"></a><a name="deletevalue"></a>CSettingsStore::DeleteValue

Löscht einen Wert `m_hKey`aus .

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>Parameter

*pszValue*<br/>
[in] Gibt das zu entfernende Wertfeld an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

## <a name="csettingsstoreopen"></a><a name="open"></a>CSettingsStore::Öffnen

Öffnet einen Registrierungsschlüssel.

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>Parameter

*pszPath*<br/>
[in] Der Name eines Registrierungsschlüssels.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Nachdem diese Methode den angegebenen Schlüssel `m_hKey` erfolgreich geöffnet hat, wird das Handle dieses Schlüssels festgelegt.

## <a name="csettingsstoreread"></a><a name="read"></a>CSettingsStore::Lesen

Liest einen Wert aus einem Schlüssel in der Registrierung.

```
virtual BOOL Read(
    LPCTSTR pszKey,
    int& iVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    DWORD& dwVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CString& sVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Read(
    LPCTSTR pszKey,
    CRect& rect);

virtual BOOL Read(
    LPCTSTR pszKey,
    BYTE** ppData,
    UINT* pBytes);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject*& pObj);
```

### <a name="parameters"></a>Parameter

*pszKey*<br/>
[in] Zeiger auf eine null-terminierte Zeichenfolge, die den Namen des Wertes enthält, der aus der Registrierung gelesen werden soll.

*iVal*<br/>
[out] Verweis auf eine Ganzzahlvariable, die den vom Registrierungsschlüssel gelesenen Wert empfängt.

*dwVal*<br/>
[out] Verweis auf eine 32-Bit-Doppelwortvariable, die den vom Registrierungsschlüssel gelesenen Wert empfängt.

*sVal*<br/>
[out] Verweis auf eine Zeichenfolgenvariable, die den vom Registrierungsschlüssel gelesenen Wert empfängt.

*scStringList*<br/>
[out] Verweis auf eine Zeichenfolgenlistenvariable, die den vom Registrierungsschlüssel gelesenen Wert empfängt.

*scArray*<br/>
[out] Verweis auf eine Zeichenfolgenarrayvariable, die den vom Registrierungsschlüssel gelesenen Wert empfängt.

*dwcArray*<br/>
[out] Verweis auf eine 32-Bit-Doppelwortarrayvariable, die den vom Registrierungsschlüssel gelesenen Wert empfängt.

*wcArray*<br/>
[out] Verweis auf eine 16-Bit-Wordarray-Variable, die den vom Registrierungsschlüssel gelesenen Wert empfängt.

*bcArray*<br/>
[out] Verweis auf eine Byte-Array-Variable, die den vom Registrierungsschlüssel gelesenen Wert empfängt.

*lpPoint*<br/>
[out] Verweis auf einen Zeiger `POINT` auf eine Struktur, die den vom Registrierungsschlüssel gelesenen Wert empfängt.

*Rect*<br/>
[out] Verweis auf eine [CRect-Variable,](../../atl-mfc-shared/reference/crect-class.md) die den vom Registrierungsschlüssel gelesenen Wert empfängt.

*ppData*<br/>
[out] Zeiger auf einen Zeiger auf Daten, die den vom Registrierungsschlüssel gelesenen Wert empfangen.

*pBytes*<br/>
[out] Zeiger auf eine nicht signierte Ganzzahlvariable. Diese Variable empfängt die Größe des Puffers, auf den *ppData* verweist.

*list*<br/>
[out] Verweis auf eine [CObList-Variable,](../../mfc/reference/coblist-class.md) die den vom Registrierungsschlüssel gelesenen Wert empfängt.

*obj*<br/>
[out] Verweis auf eine [CObject-Variable,](../../mfc/reference/cobject-class.md) die den vom Registrierungsschlüssel gelesenen Wert empfängt.

*pObj*<br/>
[out] Verweis auf einen Zeiger `CObject` auf eine Variable, die den vom Registrierungsschlüssel gelesenen Wert empfängt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

`Read`sucht *pszKey* als Unterschlüssel `m_hKey`von .

## <a name="csettingsstorewrite"></a><a name="write"></a>CSettingsStore::Schreiben

Schreibt einen Wert in die Registrierung unter dem geöffneten Schlüssel.

```
virtual BOOL Write(
    LPCTSTR pszKey,
    int iVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    DWORD dwVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPCTSTR pszVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Write(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    const CRect& rect);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPBYTE pData,
    UINT nBytes);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject* pObj);
```

### <a name="parameters"></a>Parameter

*pszKey*<br/>
[in] Zeiger auf eine Zeichenfolge, die den Namen des festzulegenden Werts enthält.

*iVal*<br/>
[in] Verweis auf eine Ganzzahlvariable, die die zu speichernden Daten enthält.

*dwVal*<br/>
[in] Verweis auf eine 32-Bit-Doppelwortvariable, die die zu speichernden Daten enthält.

*pszVal*<br/>
[in] Zeiger auf eine null-terminierte Zeichenfolgenvariable, die die zu speichernden Daten enthält.

*scStringList*<br/>
[in] Verweis auf eine [CStringList-Variable,](../../mfc/reference/cstringlist-class.md) die die zu speichernden Daten enthält.

*bcArray*<br/>
[in] Verweis auf eine Byte-Array-Variable, die die zu speichernden Daten enthält.

*scArray*<br/>
[in] Verweis auf eine Zeichenfolgenarrayvariable, die die zu speichernden Daten enthält.

*dwcArray*<br/>
[in] Verweis auf eine 32-Bit-Doppelwortarrayvariable, die die zu speichernden Daten enthält.

*wcArray*<br/>
[in] Verweis auf eine 16-Bit-Wortarrayvariable, die die zu speichernden Daten enthält.

*Rect*<br/>
[in] Verweis auf eine [CRect-Variable,](../../atl-mfc-shared/reference/crect-class.md) die die zu speichernden Daten enthält.

*lpPoint*<br/>
[in] Verweis auf einen Zeiger `POINT` auf eine Variable, die die zu speichernden Daten enthält.

*pData*<br/>
[in] Zeiger auf einen Puffer, der die zu speichernden Daten enthält.

*nBytes*<br/>
[in] Gibt die Größe der Daten, auf die der *pData-Parameter* zeigt, in Bytes an.

*list*<br/>
[in] Verweis auf eine [CObList-Variable,](../../mfc/reference/coblist-class.md) die die zu speichernden Daten enthält.

*obj*<br/>
[in] Verweis auf eine [CObject-Variable,](../../mfc/reference/cobject-class.md) die die zu speichernden Daten enthält.

*pObj*<br/>
[in] Zeiger auf einen Zeiger `CObject` auf eine Variable, die die zu speichernden Daten enthält.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Um in die Registrierung zu schreiben, müssen Sie *bReadOnly* beim Erstellen eines [CSettingsStore-Objekts](../../mfc/reference/csettingsstore-class.md) auf einen Wert ungleich Null festlegen. Weitere Informationen finden Sie unter [CSettingsStore::CSettingsStore](#csettingsstore).

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx-Klasse](../../mfc/reference/cwinappex-class.md)
