---
title: CComBSTR-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComBSTR
- ATLBASE/ATL::CComBSTR
- ATLBASE/ATL::CComBSTR::CComBSTR
- ATLBASE/ATL::CComBSTR::Append
- ATLBASE/ATL::CComBSTR::AppendBSTR
- ATLBASE/ATL::CComBSTR::AppendBytes
- ATLBASE/ATL::CComBSTR::ArrayToBSTR
- ATLBASE/ATL::CComBSTR::AssignBSTR
- ATLBASE/ATL::CComBSTR::Attach
- ATLBASE/ATL::CComBSTR::BSTRToArray
- ATLBASE/ATL::CComBSTR::ByteLength
- ATLBASE/ATL::CComBSTR::Copy
- ATLBASE/ATL::CComBSTR::CopyTo
- ATLBASE/ATL::CComBSTR::Detach
- ATLBASE/ATL::CComBSTR::Empty
- ATLBASE/ATL::CComBSTR::Length
- ATLBASE/ATL::CComBSTR::LoadString
- ATLBASE/ATL::CComBSTR::ReadFromStream
- ATLBASE/ATL::CComBSTR::ToLower
- ATLBASE/ATL::CComBSTR::ToUpper
- ATLBASE/ATL::CComBSTR::WriteToStream
- ATLBASE/ATL::CComBSTR::m_str
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
ms.openlocfilehash: adaad47c49a64c6654b70fa60ef5514e104c50a5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321056"
---
# <a name="ccombstr-class"></a>CComBSTR-Klasse

Diese Klasse ist ein Wrapper für [BSTR](/previous-versions/windows/desktop/automat/bstr)s.

## <a name="syntax"></a>Syntax

```
class CComBSTR
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComBSTR::CComBSTR](#ccombstr)|Der Konstruktor.|
|[CComBSTR::-CComBSTR](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComBSTR::Anfügen](#append)|Appends a string to `m_str`.|
|[CComBSTR::AnfügenBSTR](#appendbstr)|Fügt einen BSTR `m_str`an an an an.|
|[CComBSTR::AnfügenBytes](#appendbytes)|Appends a specified number of bytes to `m_str`.|
|[CComBSTR::ArrayToBSTR](#arraytobstr)|Erstellt einen BSTR aus dem ersten Zeichen jedes Elements im `CComBSTR` safearray und fügt ihn an das Objekt an.|
|[CComBSTR::AssignBSTR](#assignbstr)|Weist einen BSTR `m_str`zu .|
|[CComBSTR::Anfügen](#attach)|Fügt dem `CComBSTR` Objekt einen BSTR an.|
|[CComBSTR::BSTRToArray](#bstrtoarray)|Erstellt ein nullbasiertes eindimensionales Safearray, bei dem jedes `CComBSTR` Element des Arrays ein Zeichen aus dem Objekt ist.|
|[CComBSTR::ByteLength](#bytelength)|Gibt die `m_str` Länge von in Bytes zurück.|
|[CComBSTR::Kopieren](#copy)|Gibt eine `m_str`Kopie von zurück.|
|[CComBSTR::CopyTo](#copyto)|Gibt eine `m_str` Kopie von über einen **[out]-Parameter** zurück|
|[CComBSTR::Detach](#detach)|Trennt sich `m_str` vom `CComBSTR` Objekt.|
|[CComBSTR::Leer](#empty)|Frees `m_str`.|
|[CComBSTR::Länge](#length)|Gibt die `m_str`Länge von zurück.|
|[CComBSTR::LoadString](#loadstring)|Lädt eine Zeichenfolgenressource.|
|[CComBSTR::ReadFromStream](#readfromstream)|Lädt ein BSTR-Objekt aus einem Stream.|
|[CComBSTR::ToLower](#tolower)|Konvertiert die Zeichenfolge in Kleinbuchstaben.|
|[CComBSTR::ToUpper](#toupper)|Konvertiert die Zeichenfolge in Großbuchstaben.|
|[CComBSTR::WriteToStream](#writetostream)|Speichert `m_str` in einem Stream.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComBSTR::operator BSTR](#operator_bstr)|Gibt ein `CComBSTR` Objekt in einen BSTR um.|
|[CComBSTR::Operator !](#operator_not)|Gibt TRUE oder FALSE `m_str`zurück, je nachdem, ob NULL ist.|
|[CComBSTR::operator !=](#operator_neq)|Vergleicht `CComBSTR` eine mit einer Zeichenfolge.|
|[CComBSTR::Operator &](#operator_amp)|Gibt die `m_str`Adresse von zurück.|
|[CComBSTR::Operator +=](#operator_add_eq)|Fügt eine `CComBSTR` an das Objekt an.|
|[CComBSTR::Operator <](#operator_lt)|Vergleicht `CComBSTR` eine mit einer Zeichenfolge.|
|[CComBSTR::Operator =](#operator_eq)|Weist einem einen `m_str`Wert zu.|
|[CComBSTR::operator ==](#operator_eq_eq)|Vergleicht `CComBSTR` eine mit einer Zeichenfolge.|
|[CComBSTR::Operator >](#operator_gt)|Vergleicht `CComBSTR` eine mit einer Zeichenfolge.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComBSTR::m_str](#m_str)|Enthält den Dem `CComBSTR` Objekt zugeordneten BSTR.|

## <a name="remarks"></a>Bemerkungen

Die `CComBSTR` Klasse ist ein Wrapper für BSTRs, bei denen es sich um Längenzeichenfolgen handelt. Die Länge wird als ganzzahlige Datei an der Speicherposition vor den Daten in der Zeichenfolge gespeichert.

Ein [BSTR](/previous-versions/windows/desktop/automat/bstr) wird nach dem zuletzt gezählten Zeichen null beendet, kann aber auch Nullzeichen enthalten, die in die Zeichenfolge eingebettet sind. Die Zeichenfolgenlänge wird durch die Zeichenanzahl bestimmt, nicht durch das erste Nullzeichen.

> [!NOTE]
> Die `CComBSTR` Klasse stellt eine Reihe von Membern (Konstruktoren, Zuweisungsoperatoren und Vergleichsoperatoren) bereit, die entweder ANSI- oder Unicode-Zeichenfolgen als Argumente verwenden. Die ANSI-Versionen dieser Funktionen sind weniger effizient als ihre Unicode-Entsprechungen, da temporäre Unicode-Zeichenfolgen häufig intern erstellt werden. Verwenden Sie die Unicode-Versionen nach Möglichkeit, um dieEffizienz zu steigern.

> [!NOTE]
> Aufgrund des verbesserten Suchverhaltens, das in Visual `bstr = L"String2" + bstr;`Studio .NET implementiert wurde, sollte Code wie `bstr = CStringW(L"String2") + bstr`, der in früheren Versionen kompiliert wurde, stattdessen als implementiert werden.

Eine Liste der Vorsichtsmaßnahmen bei der Verwendung `CComBSTR`finden Sie unter [Programmieren mit CComBSTR](../../atl/programming-with-ccombstr-atl.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="ccombstrappend"></a><a name="append"></a>CComBSTR::Anfügen

Fügt entweder *lpsz* oder das BSTR-Mitglied von *bstrSrc* an [m_str](#m_str)an.

```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parameter

*bstrSrc*<br/>
[in] Ein `CComBSTR` anzuhängendes Objekt.

*Ch*<br/>
[in] Ein Zeichen, das angehängt werden soll.

*lpsz*<br/>
[in] Eine null-terminierte Zeichenfolge, die angehängt werden soll. Sie können eine Unicode-Zeichenfolge über die LPCOLESTR-Überladung oder eine ANSI-Zeichenfolge über die LPCSTR-Version übergeben.

*nLen*<br/>
[in] Die Anzahl der Zeichen von *lpsz* zum Anfügen.

### <a name="return-value"></a>Rückgabewert

S_OK auf Erfolg oder einen beliebigen HRESULT-Standardfehlerwert.

### <a name="remarks"></a>Bemerkungen

Eine ANSI-Zeichenfolge wird vor dem Anfügen in Unicode konvertiert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

## <a name="ccombstrappendbstr"></a><a name="appendbstr"></a>CComBSTR::AnfügenBSTR

Fügt den angegebenen BSTR an [m_str](#m_str)an.

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
[in] Ein BSTR zum Anhängen.

### <a name="return-value"></a>Rückgabewert

S_OK auf Erfolg oder einen beliebigen HRESULT-Standardfehlerwert.

### <a name="remarks"></a>Bemerkungen

Übergeben Sie keine gewöhnliche Breitzeichenzeichenfolge an diese Methode. Der Compiler kann den Fehler nicht abfangen, und Es treten Laufzeitfehler auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

## <a name="ccombstrappendbytes"></a><a name="appendbytes"></a>CComBSTR::AnfügenBytes

Fügt die angegebene Anzahl von Bytes ohne Konvertierung an [m_str](#m_str) an.

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parameter

*lpsz*<br/>
[in] Ein Zeiger auf ein Array von Bytes, das angehängt werden soll.

*P*<br/>
[in] Die Anzahl der anfügenden Bytes.

### <a name="return-value"></a>Rückgabewert

S_OK auf Erfolg oder einen beliebigen HRESULT-Standardfehlerwert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

## <a name="ccombstrarraytobstr"></a><a name="arraytobstr"></a>CComBSTR::ArrayToBSTR

Gibt jede vorhandene Zeichenfolge `CComBSTR` frei, die im Objekt gehalten wird, erstellt dann einen BSTR aus `CComBSTR` dem ersten Zeichen jedes Elements im safearray und fügt ihn an das Objekt an.

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>Parameter

*pSrc*<br/>
[in] Das safearray, das die Elemente enthält, die zum Erstellen der Zeichenfolge verwendet werden.

### <a name="return-value"></a>Rückgabewert

S_OK auf Erfolg oder einen beliebigen HRESULT-Standardfehlerwert.

## <a name="ccombstrassignbstr"></a><a name="assignbstr"></a>CComBSTR::AssignBSTR

Weist [m_str](#m_str)einen BSTR zu.

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>Parameter

*bstrSrc*<br/>
[in] Ein BSTR, der `CComBSTR` dem aktuellen Objekt zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

S_OK auf Erfolg oder einen beliebigen HRESULT-Standardfehlerwert.

## <a name="ccombstrattach"></a><a name="attach"></a>CComBSTR::Anfügen

Fügt dem `CComBSTR` Objekt einen BSTR an, indem der [m_str](#m_str) Member auf *src*gesetzt wird.

```
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>Parameter

*src*<br/>
[in] Der Anfügen des BSTR an das Objekt.

### <a name="remarks"></a>Bemerkungen

Übergeben Sie keine gewöhnliche Breitzeichenzeichenfolge an diese Methode. Der Compiler kann den Fehler nicht abfangen, und Es treten Laufzeitfehler auf.

> [!NOTE]
> Diese Methode bestätigt, ob es `m_str` sich um nicht-NULL handelt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

## <a name="ccombstrbstrtoarray"></a><a name="bstrtoarray"></a>CComBSTR::BSTRToArray

Erstellt ein nullbasiertes eindimensionales Safearray, bei dem jedes `CComBSTR` Element des Arrays ein Zeichen aus dem Objekt ist.

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>Parameter

*ppArray*<br/>
[out] Der Zeiger auf das safearray, das verwendet wird, um die Ergebnisse der Funktion zu halten.

### <a name="return-value"></a>Rückgabewert

S_OK auf Erfolg oder einen beliebigen HRESULT-Standardfehlerwert.

## <a name="ccombstrbytelength"></a><a name="bytelength"></a>CComBSTR::ByteLength

Gibt die Anzahl `m_str`der Bytes in zurück, mit Ausnahme des beendenden Nullzeichens.

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Länge [m_str](#m_str) des m_str-Members in Bytes.

### <a name="remarks"></a>Bemerkungen

Gibt 0 `m_str` zurück, wenn null ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

## <a name="ccombstrccombstr"></a><a name="ccombstr"></a>CComBSTR::CComBSTR

Der Konstruktor. Der Standardkonstruktor legt den [m_str-Member](#m_str) auf NULL fest.

```
CComBSTR() throw();
CComBSTR(const CComBSTR& src);
CComBSTR(REFGUID  guid);
CComBSTR(int nSize);
CComBSTR(int nSize, LPCOLESTR sz);
CComBSTR(int nSize, LPCSTR sz);
CComBSTR(LPCOLESTR pSrc);
CComBSTR(LPCSTR pSrc);
CComBSTR(CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="parameters"></a>Parameter

*nGröße*<br/>
[in] Die Anzahl der Zeichen, die von *sz* kopiert `CComBSTR`werden sollen, oder die Anfangsgröße in Zeichen für die .

*Sz*<br/>
[in] Eine zu kopierende Zeichenfolge. Die Unicode-Version gibt eine LPCOLESTR-Version an. Die ANSI-Version gibt einen LPCSTR an.

*pSrc*<br/>
[in] Eine zu kopierende Zeichenfolge. Die Unicode-Version gibt eine LPCOLESTR-Version an. Die ANSI-Version gibt einen LPCSTR an.

*src*<br/>
[in] Ein `CComBSTR`-Objekt.

*guid*<br/>
[in] Ein Verweis `GUID` auf eine Struktur.

### <a name="remarks"></a>Bemerkungen

Der Kopierkonstruktor wird auf eine Kopie des BSTR-Members von `m_str` *src*festgelegt. Der `REFGUID` Konstruktor konvertiert die GUID `StringFromGUID2` mithilfe einer Zeichenfolge und speichert das Ergebnis.

Die anderen Konstruktoren legen `m_str` auf eine Kopie der angegebenen Zeichenfolge fest. Wenn Sie einen Wert für *nSize*übergeben, werden nur *nSize-Zeichen* kopiert, gefolgt von einem beendenden Nullzeichen.

`CComBSTR` unterstützt die move-Semantik. Mit dem Bewegungskonstruktor (dem Konstruktor, der einen rvalue-Verweis verwendet (`&&`) können Sie ein neues Objekt erstellen, das die Daten des alten als Argument übergebenen Objekts verwendet, ohne das Objekt kopieren zu müssen.

Der Destruktor gibt die Zeichenfolge frei, auf die von `m_str` gezeigt wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

## <a name="ccombstrccombstr"></a><a name="dtor"></a>CComBSTR::-CComBSTR

Der Destruktor.

```
~CComBSTR();
```

### <a name="remarks"></a>Bemerkungen

Der Destruktor gibt die Zeichenfolge frei, auf die von `m_str` gezeigt wird.

## <a name="ccombstrcopy"></a><a name="copy"></a>CComBSTR::Kopieren

Ordnet eine Kopie von `m_str`zu und gibt sie zurück.

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>Rückgabewert

Eine Kopie [m_str](#m_str) des m_str-Mitglieds. Wenn `m_str` NULL ist, gibt NULL zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

## <a name="ccombstrcopyto"></a><a name="copyto"></a>CComBSTR::CopyTo

Ordnet eine Kopie des [m_str](#m_str) über den Parameter zu und gibt diese zurück.

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>Parameter

*pbstr*<br/>
[out] Die Adresse eines BSTR, in dem die von dieser Methode zugewiesene Zeichenfolge zurückgegeben werden soll.

*pvarDest*<br/>
[out] Die Adresse eines VARIANT, in dem die von dieser Methode zugewiesene Zeichenfolge zurückgegeben werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert, der den Erfolg oder Misserfolg der Kopie angibt.

### <a name="remarks"></a>Bemerkungen

Nach dem Aufruf dieser Methode ist der VARIANT, auf den von *pvarDest* verwiesen wird, vom Typ VT_BSTR.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

## <a name="ccombstrdetach"></a><a name="detach"></a>CComBSTR::Detach

Trennt [m_str](#m_str) vom `CComBSTR` Objekt und `m_str` setzt auf NULL.

```
BSTR Detach() throw();
```

### <a name="return-value"></a>Rückgabewert

Der dem `CComBSTR` Objekt zugeordnete BSTR.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

## <a name="ccombstrempty"></a><a name="empty"></a>CComBSTR::Leer

Befreit das [m_str](#m_str) m_str-Mitglied.

```
void Empty() throw();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

## <a name="ccombstrlength"></a><a name="length"></a>CComBSTR::Länge

Gibt die Anzahl `m_str`der Zeichen in zurück, mit Ausnahme des beendenden Nullzeichens.

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Länge [m_str](#m_str) des m_str-Mitglieds.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

## <a name="ccombstrloadstring"></a><a name="loadstring"></a>CComBSTR::LoadString

Lädt eine von *nID* angegebene Zeichenfolgenressource und speichert sie in diesem Objekt.

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>Parameter

Siehe [LoadString](/windows/win32/api/winuser/nf-winuser-loadstringw) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Zeichenfolge erfolgreich geladen wurde. Andernfalls wird FALSE zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die erste Funktion lädt die Ressource aus dem von Ihnen identifizierten Modul über den Parameter *hInst.* Die zweite Funktion lädt die Ressource aus dem Ressourcenmodul, das dem in diesem Projekt verwendeten [CComModule -abgeleiteten](../../atl/reference/ccommodule-class.md)Objekt zugeordnet ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

## <a name="ccombstrm_str"></a><a name="m_str"></a>CComBSTR::m_str

Enthält den Dem `CComBSTR` Objekt zugeordneten BSTR.

```
BSTR m_str;
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

## <a name="ccombstroperator-bstr"></a><a name="operator_bstr"></a>CComBSTR::operator BSTR

Gibt ein `CComBSTR` Objekt in einen BSTR um.

```
operator BSTR() const throw();
```

### <a name="remarks"></a>Bemerkungen

Ermöglicht das `CComBSTR` Übergeben von Objekten an Funktionen mit **[in]** BSTR-Parametern.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CComBSTR::m_str](#m_str).

## <a name="ccombstroperator-"></a><a name="operator_not"></a>CComBSTR::Operator !

Überprüft, ob die BSTR-Zeichenfolge NULL ist.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das [m_str-Member](#m_str) NULL ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Dieser Operator sucht nur nach einem NULL-Wert, nicht nach einer leeren Zeichenfolge.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

## <a name="ccombstroperator-"></a><a name="operator_neq"></a>CComBSTR::operator !=

Gibt das logische Gegenteil des [Operators ==](#operator_eq_eq)zurück.

```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```

### <a name="parameters"></a>Parameter

*bstrSrc*<br/>
[in] Ein `CComBSTR`-Objekt.

*pszSrc*<br/>
[in] Eine Null-Termin-Zeichenfolge.

*nNull*<br/>
[in] Muss NULL sein.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das verglichene Element nicht gleich dem `CComBSTR` Objekt ist. Andernfalls wird FALSE zurückgegeben.

### <a name="remarks"></a>Bemerkungen

`CComBSTR`werden textlich im Kontext des Standardgebietsschemas des Benutzers verglichen. Der endgültige Vergleichsoperator vergleicht nur die enthaltene Zeichenfolge mit NULL.

## <a name="ccombstroperator-amp"></a><a name="operator_amp"></a>CComBSTR::Operator&amp;

Gibt die Adresse des im [m_str-Members](#m_str) gespeicherten BSTR zurück.

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>Bemerkungen

`CComBstr operator &`hat eine spezielle Behauptung zugeordnet, um Speicherverluste zu identifizieren. Das Programm bestätigt, `m_str` wenn das Mitglied initialisiert wird. Diese Assertion wurde erstellt, um Situationen `& operator` zu identifizieren, in `m_str` denen ein Programmierer `m_str`die verwendet, um dem Member einen neuen Wert zuzuweisen, ohne die erste Zuweisung von freizugeben. Wenn `m_str` null NULL ist, geht das Programm davon aus, dass m_str noch nicht zugewiesen wurde. In diesem Fall wird das Programm nicht bestätigen.

Diese Assertion ist standardmäßig nicht aktiviert. Definieren Sie ATL_CCOMBSTR_ADDRESS_OF_ASSERT, um diese Assertion zu aktivieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

## <a name="ccombstroperator-"></a><a name="operator_add_eq"></a>CComBSTR::Operator +=

Fügt eine Zeichenfolge `CComBSTR` an das Objekt an.

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>Parameter

*bstrSrc*<br/>
[in] Ein `CComBSTR` anzuhängendes Objekt.

*pszSrc*<br/>
[in] Eine Null-Termin-Zeichenfolge, die angehängt werden soll.

### <a name="remarks"></a>Bemerkungen

`CComBSTR`werden textlich im Kontext des Standardgebietsschemas des Benutzers verglichen. Der LPCOLESTR-Vergleich `memcmp` wird anhand der Rohdaten in jeder Zeichenfolge durchgeführt. Der LPCSTR-Vergleich wird auf die gleiche Weise durchgeführt, sobald eine temporäre Unicode-Kopie von *pszSrc* erstellt wurde. Der endgültige Vergleichsoperator vergleicht nur die enthaltene Zeichenfolge mit NULL.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

## <a name="ccombstroperator-lt"></a><a name="operator_lt"></a>CComBSTR::Operator&lt;

Vergleicht `CComBSTR` eine mit einer Zeichenfolge.

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das `CComBSTR` verglichene Element kleiner als das Objekt ist. Andernfalls wird FALSE zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Der Vergleich wird mit dem Standardgebietsschema des Benutzers durchgeführt.

## <a name="ccombstroperator-"></a><a name="operator_eq"></a>CComBSTR::Operator =

Legt das [m_str-Member](#m_str) auf eine Kopie von *pSrc* oder auf eine Kopie des BSTR-Members von *src fest.* Der Bewegungszuweisungsoperator wird verschoben, `src` ohne ihn zu kopieren.

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>Bemerkungen

Der *pSrc-Parameter* gibt entweder eine LPCOLESTR für Unicode-Versionen oder LPCSTR für ANSI-Versionen an.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CComBSTR::Copy](#copy).

## <a name="ccombstroperator-"></a><a name="operator_eq_eq"></a>CComBSTR::operator ==

Vergleicht `CComBSTR` eine mit einer Zeichenfolge. `CComBSTR`werden textlich im Kontext des Standardgebietsschemas des Benutzers verglichen.

```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```

### <a name="parameters"></a>Parameter

*bstrSrc*<br/>
[in] Ein `CComBSTR`-Objekt.

*pszSrc*<br/>
[in] Eine Null-Termin-Zeichenfolge.

*nNull*<br/>
[in] Muss NULL sein.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das `CComBSTR` verglichene Element gleich dem Objekt ist. Andernfalls wird FALSE zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Der endgültige Vergleichsoperator vergleicht nur die enthaltene Zeichenfolge mit NULL.

## <a name="ccombstroperator-gt"></a><a name="operator_gt"></a>CComBSTR::Operator&gt;

Vergleicht `CComBSTR` eine mit einer Zeichenfolge.

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das `CComBSTR` verglichene Element größer als das Objekt ist. Andernfalls wird FALSE zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Der Vergleich wird mit dem Standardgebietsschema des Benutzers durchgeführt.

## <a name="ccombstrreadfromstream"></a><a name="readfromstream"></a>CComBSTR::ReadFromStream

Legt den [m_str-Member](#m_str) auf den Im angegebenen Stream enthaltenen BSTR fest.

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parameter

*pStream*<br/>
[in] Ein Zeiger auf die [IStream-Schnittstelle](/windows/win32/api/objidl/nn-objidl-istream) im Stream, der die Daten enthält.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

`ReadToStream`erfordert, dass der Inhalt des Streams an der aktuellen Position mit dem Datenformat kompatibel ist, das durch einen Aufruf von [WriteToStream](#writetostream)geschrieben wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

## <a name="ccombstrtolower"></a><a name="tolower"></a>CComBSTR::ToLower

Konvertiert die enthaltene Zeichenfolge in Kleinbuchstaben.

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Weitere `CharLowerBuff` Informationen zur Durchgeführt-Konvertierung finden Sie unter .

## <a name="ccombstrtoupper"></a><a name="toupper"></a>CComBSTR::ToUpper

Konvertiert die enthaltene Zeichenfolge in Großbuchstaben.

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Weitere `CharUpperBuff` Informationen zur Durchgeführt-Konvertierung finden Sie unter .

## <a name="ccombstrwritetostream"></a><a name="writetostream"></a>CComBSTR::WriteToStream

Speichert das [m_str-Member](#m_str) in einem Stream.

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parameter

*pStream*<br/>
[in] Ein Zeiger auf die [IStream-Schnittstelle](/windows/win32/api/objidl/nn-objidl-istream) in einem Stream.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Sie können einen BSTR aus dem Inhalt des Streams mit der [ReadFromStream-Funktion](#readfromstream) neu erstellen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[ATL- und MFC-Zeichenfolgenkonvertierungsmakros](string-conversion-macros.md)
