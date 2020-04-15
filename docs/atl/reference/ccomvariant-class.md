---
title: CComVariant-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComVariant
- ATLCOMCLI/ATL::CComVariant
- ATLCOMCLI/ATL::CComVariant::CComVariant
- ATLCOMCLI/ATL::CComVariant::Attach
- ATLCOMCLI/ATL::CComVariant::ChangeType
- ATLCOMCLI/ATL::CComVariant::Clear
- ATLCOMCLI/ATL::CComVariant::Copy
- ATLCOMCLI/ATL::CComVariant::CopyTo
- ATLCOMCLI/ATL::CComVariant::Detach
- ATLCOMCLI/ATL::CComVariant::GetSize
- ATLCOMCLI/ATL::CComVariant::ReadFromStream
- ATLCOMCLI/ATL::CComVariant::SetByRef
- ATLCOMCLI/ATL::CComVariant::WriteToStream
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
ms.openlocfilehash: 9a84d91e20242fb206d1d3f71fcb3dd207561f62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327232"
---
# <a name="ccomvariant-class"></a>CComVariant-Klasse

Diese Klasse umschließt den VARIANT-Typ und stellt einen Member bereit, der den Typ der gespeicherten Daten angibt.

## <a name="syntax"></a>Syntax

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComVariant::CComVariant](#ccomvariant)|Der Konstruktor.|
|[CComVariant::-cComVariant](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComVariant::Anfügen](#attach)|Fügt dem `CComVariant` Objekt einen VARIANT an.|
|[CComVariant::ChangeType](#changetype)|Konvertiert das `CComVariant` Objekt in einen neuen Typ.|
|[CComVariant::Löschen](#clear)|Löscht das `CComVariant` Objekt.|
|[CComVariant::Kopieren](#copy)|Kopiert einen VARIANT `CComVariant` in das Objekt.|
|[CComVariant::CopyTo](#copyto)|Kopiert den Inhalt `CComVariant` des Objekts.|
|[CComVariant::Detach](#detach)|Trennt den zugrunde liegenden `CComVariant` VARIANT vom Objekt.|
|[CComVariant::GetSize](#getsize)|Gibt die Größe in Anzahl der `CComVariant` Bytes des Inhalts des Objekts zurück.|
|[CComVariant::ReadFromStream](#readfromstream)|Lädt einen VARIANT aus einem Stream.|
|[CComVariant::SetByRef](#setbyref)|Initialisiert das `CComVariant` Objekt und `vt` legt fest, dass das Element VT_BYREF.|
|[CComVariant::WriteToStream](#writetostream)|Speichert den zugrunde liegenden VARIANT in einem Stream.|

### <a name="public-operators"></a>Öffentliche Operatoren

|||
|-|-|
|[CComVariant::operator <](#operator_lt)|Gibt an, ob das `CComVariant` Objekt kleiner als das angegebene VARIANT ist.|
|[CComVariant::operator >](#operator_gt)|Gibt an, ob das `CComVariant` Objekt größer als der angegebene VARIANT ist.|
|[Operator !=](#operator_neq)|Gibt an, ob das `CComVariant` Objekt nicht dem angegebenen VARIANT entspricht.|
|[Operator =](#operator_eq)|Weist dem `CComVariant` Objekt einen Wert zu.|
|[Operator ==](#operator_eq_eq)|Gibt an, ob das `CComVariant` Objekt dem angegebenen VARIANT entspricht.|

## <a name="remarks"></a>Bemerkungen

`CComVariant`umschließt den Typ VARIANT und VARIANTARG, der aus einer Union und einem Member besteht, der den Typ der in der Union gespeicherten Daten angibt. VARIANTs werden in der Regel in der Automatisierung verwendet.

`CComVariant`vom Variant-Typ ableitet, so dass er überall dort verwendet werden kann, wo ein VARIANT verwendet werden kann. Sie können z. B. das V_VT-Makro `CComVariant` verwenden, um `vt` den Typ eines zu extrahieren, oder Sie können direkt auf das Element zugreifen, genau wie Sie es mit einem VARIANT können.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcomcli.h

## <a name="ccomvariantattach"></a><a name="attach"></a>CComVariant::Anfügen

Löscht sicher den aktuellen `CComVariant` Inhalt des Objekts, kopiert den Inhalt von *pSrc* in dieses Objekt und legt dann den Variantentyp von *pSrc* auf VT_EMPTY.

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>Parameter

*pSrc*<br/>
[in] Zeigt auf den [VARIANT,](/windows/win32/api/oaidl/ns-oaidl-variant) der dem Objekt zugeordnet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Das Eigentum an den daten, die `CComVariant` sich im Besitz von *pSrc* befinden, wird auf das Objekt übertragen.

## <a name="ccomvariantccomvariant"></a><a name="ccomvariant"></a>CComVariant::CComVariant

Jeder Konstruktor verarbeitet die sichere `CComVariant` Initialisierung des `VariantInit` Objekts, indem er die Win32-Funktion aufruft oder den Wert und Typ des Objekts entsprechend den übergebenen Parametern festlegt.

```
CComVariant() throw();
CComVariant(const CComVariant& varSrc);
CComVariant(const VARIANT& varSrc);
CComVariant(LPCOLESTR lpszSrc);
CComVariant(LPCSTR lpszSrc);
CComVariant(bool bSrc);
CComVariant(BYTE nSrc) throw();
CComVariant(int nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned int  nSrc, VARTYPE vtSrc = VT_UI4) throw();
CComVariant(shor  nSrc) throw();
CComVariant(unsigned short nSrc) throw();
CComVariant(long  nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned long  nSrc) throw();
CComVariant(LONGLONG  nSrc) throw();
CComVariant(ULONGLONG  nSrc) throw();
CComVariant(float  fltSrc) throw();
CComVariant(double  dblSrc, VARTYPE vtSrc = VT_R8) throw();
CComVariant(CY  cySrc) throw();
CComVariant(IDispatch* pSrc) throw();
CComVariant(IUnknown* pSrc) throw();
CComVariant(const SAFEARRAY* pSrc);
CComVariant(char  cSrc) throw();
CComVariant(const CComBSTR& bstrSrc);
```

### <a name="parameters"></a>Parameter

*varSrc*<br/>
[in] Der `CComVariant` oder VARIANT, der `CComVariant` zum Initialisieren des Objekts verwendet wird. Der Inhalt der Quellvariante wird ohne Konvertierung in das Ziel kopiert.

*lpszSrc*<br/>
[in] Die Zeichenfolge, die zum `CComVariant` Initialisieren des Objekts verwendet wird. Sie können eine Zero-Terminate-Wide (Unicode)-Zeichenfolge an die LPCOLESTR-Version des Konstruktors oder eine ANSI-Zeichenfolge an die LPCSTR-Version übergeben. In beiden Fällen wird die Zeichenfolge in einen `SysAllocString`Unicode-BSTR konvertiert, der mit zugeordnet ist. Der Typ `CComVariant` des Objekts wird VT_BSTR.

*bSrc*<br/>
[in] Der **bool,** der `CComVariant` zum Initialisieren des Objekts verwendet wird. Das **bool-Argument** wird in ein VARIANT_BOOL konvertiert, bevor es gespeichert wird. Der Typ `CComVariant` des Objekts wird VT_BOOL.

*nSrc*<br/>
[in] Die **int**, **BYTE**, **short**, **long**, LONGLONG, ULONGLONG, **unsigned short**, `CComVariant` **unsigned long**, oder **unsigned int** used to initialize the object. Der Typ `CComVariant` des Objekts wird VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 oder VT_UI4.

*vtSrc*<br/>
[in] Der Typ der Variante. Wenn der erste Parameter **int**ist, werden gültige Typen VT_I4 und VT_INT. Wenn der erste Parameter **lang**ist, werden gültige Typen VT_I4 und VT_ERROR. Wenn der erste Parameter **doppelt**ist, werden gültige Typen VT_R8 und VT_DATE. Wenn der erste Parameter **int nicht signiert**ist, werden gültige Typen VT_UI4 und VT_UINT.

*fltSrc*<br/>
[in] Der **float,** der `CComVariant` zum Initialisieren des Objekts verwendet wird. Der Typ `CComVariant` des Objekts wird VT_R4.

*dblSrc*<br/>
[in] Das **Double,** das `CComVariant` zum Initialisieren des Objekts verwendet wird. Der Typ `CComVariant` des Objekts wird VT_R8.

*cySrc*<br/>
[in] Der `CY` wird verwendet, `CComVariant` um das Objekt zu initialisieren. Der Typ `CComVariant` des Objekts wird VT_CY.

*pSrc*<br/>
[in] Der `IDispatch` `IUnknown` oder der Zeiger, `CComVariant` der zum Initialisieren des Objekts verwendet wird. `AddRef`wird auf dem Schnittstellenzeiger aufgerufen. Der Typ `CComVariant` des Objekts wird VT_DISPATCH bzw. VT_UNKNOWN.

Oder der SAFERRAY-Zeiger, der `CComVariant` zum Initialisieren des Objekts verwendet wird. Eine Kopie des SAFEARRAY wird `CComVariant` im Objekt gespeichert. Der Objekttyp `CComVariant` ist eine Kombination aus dem ursprünglichen Typ des SAFEARRAY und VT_ARRAY.

*Csrc*<br/>
[in] Das **Zeichen,** das `CComVariant` zum Initialisieren des Objekts verwendet wird. Der Typ `CComVariant` des Objekts wird VT_I1.

*bstrSrc*<br/>
[in] Der BSTR, der `CComVariant` zum Initialisieren des Objekts verwendet wird. Der Typ `CComVariant` des Objekts wird VT_BSTR.

### <a name="remarks"></a>Bemerkungen

Der Destruktor verwaltet die Bereinigung, indem er [CComVariant::Clear](#clear)aufruft.

## <a name="ccomvariantccomvariant"></a><a name="dtor"></a>CComVariant::-cComVariant

Der Destruktor.

```
~CComVariant() throw();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode verwaltet die Bereinigung durch Aufrufen von [CComVariant::Clear](#clear).

## <a name="ccomvariantchangetype"></a><a name="changetype"></a>CComVariant::ChangeType

Konvertiert das `CComVariant` Objekt in einen neuen Typ.

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>Parameter

*vtNeu*<br/>
[in] Der neue Typ `CComVariant` für das Objekt.

*pSrc*<br/>
[in] Ein Zeiger auf den VARIANT, dessen Wert in den neuen Typ konvertiert wird. Der Standardwert ist NULL, d. h. das `CComVariant` Objekt wird an Ort und Stelle konvertiert.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Wenn Sie einen Wert für `ChangeType` *pSrc*übergeben, wird dieser VARIANT als Quelle für die Konvertierung verwendet. Andernfalls ist `CComVariant` das Objekt die Quelle.

## <a name="ccomvariantclear"></a><a name="clear"></a>CComVariant::Löschen

Löscht das `CComVariant` Objekt, `VariantClear` indem die Win32-Funktion aufgerufen wird.

```
HRESULT Clear();
```

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Der Destruktor `Clear`ruft automatisch auf.

## <a name="ccomvariantcopy"></a><a name="copy"></a>CComVariant::Kopieren

Gibt das `CComVariant` Objekt frei und weist ihm dann eine Kopie des angegebenen VARIANT zu.

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>Parameter

*pSrc*<br/>
[in] Ein Zeiger auf den zu kopierenden [VARIANT.](/windows/win32/api/oaidl/ns-oaidl-variant)

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="ccomvariantcopyto"></a><a name="copyto"></a>CComVariant::CopyTo

Kopiert den Inhalt `CComVariant` des Objekts.

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>Parameter

*pstrDest*<br/>
Zeigt auf einen BSTR, der eine Kopie `CComVariant` des Inhalts des Objekts erhält.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Das `CComVariant` Objekt muss vom Typ VT_BSTR sein.

## <a name="ccomvariantdetach"></a><a name="detach"></a>CComVariant::Detach

Trennt den zugrunde liegenden `CComVariant` VARIANT vom Objekt und legt den Objekttyp auf VT_EMPTY fest.

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>Parameter

*pDest*<br/>
[out] Gibt den zugrunde liegenden VARIANT-Wert des Objekts zurück.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass der Inhalt des VARIANT, auf das von *pDest* verwiesen `CComVariant` wird, automatisch gelöscht wird, bevor der Wert und der Typ des aufrufenden Objekts zugewiesen werden.

## <a name="ccomvariantgetsize"></a><a name="getsize"></a>CComVariant::GetSize

Bei VARIANTs mit einfacher fester Größe gibt diese Methode die **Größe des** zugrunde liegenden Datentyps plus **sizeof (VARTYPE)** zurück.

```
ULONG GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe in Bytes des `CComVariant` aktuellen Inhalts des Objekts.

### <a name="remarks"></a>Bemerkungen

Wenn der VARIANT einen Schnittstellenzeiger `GetSize` `IPersistStream` enthält, werden Abfragen für oder `IPersistStreamInit`. Bei Erfolg ist der Rückgabewert der 32 Bit niedriger `GetSizeMax` Ordnung des Werts, der von plus der **Größe** einer CLSID und **sizeof(VARTYPE)** zurückgegeben wird. Wenn der Schnittstellenzeiger NULL `GetSize` ist, gibt die **Größe** einer CLSID plus **sizeof (VARTYPE)** zurück. Wenn die Gesamtgröße größer `GetSize` als ULONG_MAX ist, gibt **sizeof(VARTYPE)** zurück, was auf einen Fehler hinweist.

In allen anderen Fällen wird ein temporärer VARIANT vom Typ VT_BSTR aus dem aktuellen VARIANT erzwungen. Die Länge dieses BSTR wird als Die Länge der Zeichenfolge plus die Länge der Zeichenfolge selbst plus die Größe des Nullzeichens plus **sizeof (VARTYPE)** berechnet. Wenn der VARIANT nicht zu einem VARIANT vom `GetSize` Typ VT_BSTR genötigt werden kann, gibt **sizeof(VARTYPE)** zurück.

Die von dieser Methode zurückgegebene Größe entspricht der Anzahl der Bytes, die von [CComVariant::WriteToStream](#writetostream) unter erfolgreichen Bedingungen verwendet werden.

## <a name="ccomvariantoperator-"></a><a name="operator_eq"></a>CComVariant::operator =

Weist dem `CComVariant` Objekt einen Wert und den entsprechenden Typ zu.

```
CComVariant& operator=(const CComVariant& varSrc);
CComVariant& operator=(const VARIANT& varSrc);
CComVariant& operator=(const CComBSTR& bstrSrc);
CComVariant& operator=(LPCOLESTR lpszSrc);
CComVariant& operator=(LPCSTR lpszSrc);
CComVariant& operator=(bool bSrc);
CComVariant& operator=(BYTE nSrc) throw();
CComVariant& operator=int nSrc) throw();
CComVariant& operator=(unsigned int nSrc) throw();
CComVariant& operator=(short nSrc) throw();
CComVariant& operator=(unsigned short nSrc) throw();
CComVariant& operator=(long nSrc) throw();
CComVariant& operator=(unsigned long nSrc) throw();
CComVariant& operator=(LONGLONG nSrc) throw();
CComVariant& operator=(ULONGLONG nSrc) throw();
CComVariant& operator=(float fltSrc) throw();
CComVariant& operator=(double dblSrc) throw();
CComVariant& operator=(CY cySrc) throw();
CComVariant& operator=(IDispatch* pSrc) throw();
CComVariant& operator=(IUnknown* pSrc) throw();
CComVariant& operator=(const SAFEARRAY* pSrc);
CComVariant& operator=(char cSrc) throw();
```

### <a name="parameters"></a>Parameter

*varSrc*<br/>
[in] Der `CComVariant` oder [VARIANT,](/windows/win32/api/oaidl/ns-oaidl-variant) der `CComVariant` dem Objekt zugewiesen werden soll. Der Inhalt der Quellvariante wird ohne Konvertierung in das Ziel kopiert.

*bstrSrc*<br/>
[in] Der BSTR, der `CComVariant` dem Objekt zugewiesen werden soll. Der Typ `CComVariant` des Objekts wird VT_BSTR.

*lpszSrc*<br/>
[in] Die Zeichenkette, die `CComVariant` dem Objekt zugewiesen werden soll. Sie können eine Zero-Terminate-Wide (Unicode)-Zeichenfolge an die LPCOLESTR-Version des Operators oder eine ANSI-Zeichenfolge an die LPCSTR-Version übergeben. In beiden Fällen wird die Zeichenfolge in einen `SysAllocString`Unicode-BSTR konvertiert, der mit zugewiesen wird. Der Typ `CComVariant` des Objekts wird VT_BSTR.

*bSrc*<br/>
[in] Der **bool,** der `CComVariant` dem Objekt zugewiesen werden soll. Das **bool-Argument** wird in ein VARIANT_BOOL konvertiert, bevor es gespeichert wird. Der Typ `CComVariant` des Objekts wird VT_BOOL.

*nSrc*<br/>
[in] Die **int**, BYTE, **short**, **long**, LONGLONG, ULONGLONG, **unsigned short**, **unsigned long**oder **unsigned int,** die dem `CComVariant` Objekt zugewiesen werden soll. Der Typ `CComVariant` des Objekts wird VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 oder VT_UI4.

*fltSrc*<br/>
[in] Der **Float,** der `CComVariant` dem Objekt zugewiesen werden soll. Der Typ `CComVariant` des Objekts wird VT_R4.

*dblSrc*<br/>
[in] Das **Double,** das `CComVariant` dem Objekt zugewiesen werden soll. Der Typ `CComVariant` des Objekts wird VT_R8.

*cySrc*<br/>
[in] Der, `CY` der dem `CComVariant` Objekt zugewiesen werden soll. Der Typ `CComVariant` des Objekts wird VT_CY.

*pSrc*<br/>
[in] Der `IDispatch` `IUnknown` oder der Zeiger, `CComVariant` der dem Objekt zugewiesen werden soll. `AddRef`wird auf dem Schnittstellenzeiger aufgerufen. Der Typ `CComVariant` des Objekts wird VT_DISPATCH bzw. VT_UNKNOWN.

Oder ein SAFEARRAY-Zeiger, der `CComVariant` dem Objekt zugewiesen werden soll. Eine Kopie des SAFEARRAY wird `CComVariant` im Objekt gespeichert. Der Objekttyp `CComVariant` ist eine Kombination aus dem ursprünglichen Typ des SAFEARRAY und VT_ARRAY.

*Csrc*<br/>
[in] Das Zeichen, das `CComVariant` dem Objekt zugewiesen werden soll. Der Typ `CComVariant` des Objekts wird VT_I1.

## <a name="ccomvariantoperator-"></a><a name="operator_eq_eq"></a>CComVariant::operator ==

Gibt an, ob das `CComVariant` Objekt dem angegebenen VARIANT entspricht.

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt TRUE zurück, wenn der Wert und der Typ von *varSrc* dem Wert bzw. dem Typ des `CComVariant` Objekts entsprechen. Andernfalls lautet der Wert FALSE. Der Operator verwendet das Standardgebietsschema des Benutzers, um den Vergleich durchzuführen.

Der Operator vergleicht nur den Wert der Variantentypen. Es vergleicht Zeichenfolgen, ganze Zahlen und Gleitkommapunkte, jedoch keine Arrays oder Datensätze.

## <a name="ccomvariantoperator-"></a><a name="operator_neq"></a>CComVariant::operator !=

Gibt an, ob das `CComVariant` Objekt nicht dem angegebenen VARIANT entspricht.

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt TRUE zurück, wenn der Wert oder Typ von *varSrc* nicht `CComVariant` gleich dem Wert bzw. dem Typ des Objekts ist. Andernfalls lautet der Wert FALSE. Der Operator verwendet das Standardgebietsschema des Benutzers, um den Vergleich durchzuführen.

Der Operator vergleicht nur den Wert der Variantentypen. Es vergleicht Zeichenfolgen, ganze Zahlen und Gleitkommapunkte, jedoch keine Arrays oder Datensätze.

## <a name="ccomvariantoperator-lt"></a><a name="operator_lt"></a>CComVariant::Operator&lt;

Gibt an, ob das `CComVariant` Objekt kleiner als das angegebene VARIANT ist.

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt TRUE zurück, `CComVariant` wenn der Wert des Objekts kleiner als der Wert von *varSrc*ist. Andernfalls lautet der Wert FALSE. Der Operator verwendet das Standardgebietsschema des Benutzers, um den Vergleich durchzuführen.

## <a name="ccomvariantoperator-gt"></a><a name="operator_gt"></a>CComVariant::Operator&gt;

Gibt an, ob das `CComVariant` Objekt größer als der angegebene VARIANT ist.

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt TRUE zurück, `CComVariant` wenn der Wert des Objekts größer als der Wert von *varSrc*ist. Andernfalls lautet der Wert FALSE. Der Operator verwendet das Standardgebietsschema des Benutzers, um den Vergleich durchzuführen.

## <a name="ccomvariantreadfromstream"></a><a name="readfromstream"></a>CComVariant::ReadFromStream

Legt den zugrunde liegenden VARIANT auf den VARIANT fest, der im angegebenen Stream enthalten ist.

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>Parameter

*pStream*<br/>
[in] Ein Zeiger auf die [IStream-Schnittstelle](/windows/win32/api/objidl/nn-objidl-istream) im Stream, der die Daten enthält.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

`ReadToStream`erfordert einen vorherigen Aufruf von [WriteToStream](#writetostream).

## <a name="ccomvariantsetbyref"></a><a name="setbyref"></a>CComVariant::SetByRef

Initialisiert das `CComVariant` Objekt und `vt` legt fest, dass das Element VT_BYREF.

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ von VARIANT, z. B. BSTR, **int**oder **char**.

*Pt*<br/>
Der Zeiger, der zum `CComVariant` Initialisieren des Objekts verwendet wird.

### <a name="remarks"></a>Bemerkungen

`SetByRef`ist eine Funktionsvorlage, die `CComVariant` das Objekt auf den Zeiger `vt` *pT* initialisiert und den Member auf VT_BYREF. Beispiel:

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

## <a name="ccomvariantwritetostream"></a><a name="writetostream"></a>CComVariant::WriteToStream

Speichert den zugrunde liegenden VARIANT in einem Stream.

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>Parameter

*pStream*<br/>
[in] Ein Zeiger auf die [IStream-Schnittstelle](/windows/win32/api/objidl/nn-objidl-istream) in einem Stream.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
