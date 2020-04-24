---
title: COleCurrency-Klasse
ms.date: 08/29/2019
f1_keywords:
- COleCurrency
- AFXDISP/COleCurrency
- AFXDISP/COleCurrency::COleCurrency
- AFXDISP/COleCurrency::Format
- AFXDISP/COleCurrency::GetStatus
- AFXDISP/COleCurrency::ParseCurrency
- AFXDISP/COleCurrency::SetCurrency
- AFXDISP/COleCurrency::SetStatus
- AFXDISP/COleCurrency::m_cur
- AFXDISP/COleCurrency::m_status
helpviewer_keywords:
- COleCurrency [MFC], COleCurrency
- COleCurrency [MFC], Format
- COleCurrency [MFC], GetStatus
- COleCurrency [MFC], ParseCurrency
- COleCurrency [MFC], SetCurrency
- COleCurrency [MFC], SetStatus
- COleCurrency [MFC], m_cur
- COleCurrency [MFC], m_status
ms.assetid: 3a36e345-303f-46fb-a57c-858274378a8d
ms.openlocfilehash: cc69143101c5d00d4f9a689bd02abdd9596e5b53
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753919"
---
# <a name="colecurrency-class"></a>COleCurrency-Klasse

Kapselt den `CURRENCY` -Datentyp der OLE-Automatisierung.

## <a name="syntax"></a>Syntax

```
class COleCurrency
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleCurrency::COleCurrency](#colecurrency)|Erstellt ein `COleCurrency`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleCurrency::Format](#format)|Generiert eine formatierte Zeichenfolgendarstellung eines `COleCurrency` Objekts.|
|[COleCurrency::GetStatus](#getstatus)|Ruft den Status (Gültigkeit) dieses Objekts `COleCurrency` ab.|
|[COleCurrency::ParseWährung](#parsecurrency)|Liest einen CURRENCY-Wert aus einer `COleCurrency`Zeichenfolge und legt den Wert von fest.|
|[COleCurrency::SetCurrency](#setcurrency)|Legt den Wert `COleCurrency` dieses Objekts fest.|
|[COleCurrency::SetStatus](#setstatus)|Legt den Status (Gültigkeit) für dieses `COleCurrency` Objekt fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Operator =](#operator_eq)|Kopiert `COleCurrency` einen Wert.|
|[Betreiber +, -](#operator_plus_minus)|Fügt das Vorzeichen von Werten `COleCurrency` hinzu, subtrahiert und ändert das Vorzeichen.|
|[Operator +=, -=](#operator_plus_minus_eq)|Fügt einen `COleCurrency` Wert von diesem `COleCurrency` Objekt hinzu und subtrahiert diesen.|
|[Betreiber */](#operator_star)|Skaliert einen `COleCurrency` Wert um einen ganzzahligen Wert.|
|[Operator *=, /=](#operator_star_div_eq)|Skaliert diesen `COleCurrency` Wert um einen Ganzzahlwert.|
|[Betreiber <<](#operator_stream)|Gibt einen `COleCurrency` Wert `CArchive` `CDumpContext`an oder aus.|
|[Betreiber >>](#operator_stream)|Gibt ein `COleCurrency` Objekt `CArchive`aus ein.|
|[Betreiber CURRENCY](#operator_currency)|Konvertiert einen `COleCurrency` Wert in eine CURRENCY.|
|[Operator ==, <, <=, etc.](#colecurrency_relational_operators)|Vergleicht `COleCurrency` zwei Werte.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleCurrency::m_cur](#m_cur)|Enthält die zugrunde `COleCurrency` liegende CURRENCY für dieses Objekt.|
|[COleCurrency::m_status](#m_status)|Enthält den Status `COleCurrency` dieses Objekts.|

## <a name="remarks"></a>Bemerkungen

`COleCurrency`hat keine Basisklasse.

CURRENCY wird als 8-Byte-Wert für zwei Komplement-Ganzzahlwerte implementiert, die um 10.000 skaliert werden. Dies ermöglicht eine Festkommazahl mit 15 Stellen links vom Dezimaltrennzeichen und 4 Ziffern rechts. Der CURRENCY-Datentyp ist äußerst nützlich für Berechnungen mit Geld oder für jede Festkommaberechnung, bei der Genauigkeit wichtig ist. Es ist einer der möglichen `VARIANT` Typen für den Datentyp der OLE-Automatisierung.

`COleCurrency`implementiert auch einige grundlegende arithmetische Operationen für diesen Festpunkttyp. Die unterstützten Vorgänge wurden ausgewählt, um die Rundungsfehler zu steuern, die bei Festkommaberechnungen auftreten.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`COleCurrency`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdisp.h

## <a name="colecurrencycolecurrency"></a><a name="colecurrency"></a>COleCurrency::COleCurrency

Erstellt ein `COleCurrency`-Objekt.

```
COleCurrency();
COleCurrency(CURRENCY cySrc);
COleCurrency(const COleCurrency& curSrc);
COleCurrency(const VARIANT& varSrc);

COleCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parameter

*cySrc*<br/>
Ein CURRENCY-Wert, der `COleCurrency` in das neue Objekt kopiert werden soll.

*curSrc*<br/>
Ein `COleCurrency` vorhandenes Objekt, das `COleCurrency` in das neue Objekt kopiert werden soll.

*varSrc*<br/>
Eine `VARIANT` vorhandene Datenstruktur `COleVariant` (möglicherweise ein Objekt), die in einen Währungswert `COleCurrency` (VT_CY) konvertiert und in das neue Objekt kopiert werden soll.

*nUnits*, *nFractionalUnits* Geben Sie die Einheiten und den Bruchteil (in 1/10.000) `COleCurrency` des Wertes an, der in das neue Objekt kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

Alle diese Konstruktoren `COleCurrency` erstellen neue Objekte, die auf den angegebenen Wert initialisiert wurden. Es folgt eine kurze Beschreibung jedes dieser Konstruktoren. Sofern nicht anders angegeben, `COleCurrency` ist der Status des neuen Elements auf gültig festgelegt.

- COleCurrency() Erstellt `COleCurrency` ein Objekt, das auf 0 (Null) initialisiert wurde.

- COleCurrency(`cySrc`) Erstellt `COleCurrency` ein Objekt aus einem [CURRENCY-Wert.](/windows/win32/api/wtypes/ns-wtypes-cy~r1)

- COleCurrency(`curSrc`) Erstellt `COleCurrency` ein Objekt `COleCurrency` aus einem vorhandenen Objekt. Das neue Objekt hat den gleichen Status wie das Quellobjekt.

- COleCurrency(`varSrc`) Erstellt `COleCurrency` ein Objekt. Versucht, eine [VARIANT-Struktur](/windows/win32/api/oaidl/ns-oaidl-variant) oder `COleVariant` ein Objekt in einen VT_CY-Wert zu konvertieren. Wenn diese Konvertierung erfolgreich ist, wird der `COleCurrency` konvertierte Wert in das neue Objekt kopiert. Ist dies nicht der `COleCurrency` Fall, wird der Wert des Objekts auf Null (0) und sein Status auf ungültig gesetzt.

- COleCurrency(`nUnits` `nFractionalUnits`, ) `COleCurrency` Erstellt ein Objekt aus den angegebenen numerischen Komponenten. Wenn der absolute Wert des Bruchteils größer als 10.000 ist, wird die entsprechende Anpassung an die Einheiten vorgenommen. Beachten Sie, dass die Einheiten und der Bruchteil durch signierte Long-Werte angegeben werden.

Weitere Informationen finden Sie in den Einträgen [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy~r1) und [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) im Windows SDK.

### <a name="example"></a>Beispiel

Die folgenden Beispiele zeigen die Auswirkungen der Nullparameter- und Zweiparameterkonstruktoren:

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

## <a name="colecurrencyformat"></a><a name="format"></a>COleCurrency::Format

Rufen Sie diese Memberfunktion auf, um eine formatierte Darstellung des Währungswerts zu erstellen.

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
Gibt Flags für Gebietsschemaeinstellungen an. Nur das folgende Flag ist für die Währung relevant:

- LOCALE_NOUSEROVERRIDE Verwenden Sie die Standardgebietsschemaeinstellungen des Systems anstelle von benutzerdefinierten Benutzereinstellungen.

*Lcid*<br/>
Gibt die Gebietsschema-ID an, die für die Konvertierung verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

A, `CString` das den formatierten Währungswert enthält.

### <a name="remarks"></a>Bemerkungen

Es formatiert den Wert mithilfe der lokalen Sprachspezifikationen (Gebietsschema-IDs). Ein Währungssymbol ist im zurückgegebenen Wert nicht enthalten. Wenn der Status `COleCurrency` dieses Objekts null ist, ist der Rückgabewert eine leere Zeichenfolge. Wenn der Status ungültig ist, wird die Rückgabezeichenfolge durch die Zeichenfolgenressource IDS_INVALID_CURRENCY angegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

## <a name="colecurrencygetstatus"></a><a name="getstatus"></a>COleCurrency::GetStatus

Rufen Sie diese Memberfunktion auf, um `COleCurrency` den Status (Gültigkeit) eines bestimmten Objekts abzurufen.

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt den Status `COleCurrency` dieses Werts zurück.

### <a name="remarks"></a>Bemerkungen

Der Rückgabewert wird `CurrencyStatus` durch den aufgezählten Typ `COleCurrency` definiert, der innerhalb der Klasse definiert ist.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Eine kurze Beschreibung dieser Statuswerte finden Sie in der folgenden Liste:

- `COleCurrency::valid`Gibt an, dass dieses `COleCurrency` Objekt gültig ist.

- `COleCurrency::invalid`Gibt an, dass dieses `COleCurrency` Objekt ungültig ist. das heißt, sein Wert kann falsch sein.

- `COleCurrency::null`Gibt an, dass dieses `COleCurrency` Objekt null ist, d. h., dass kein Wert für dieses Objekt angegeben wurde. (Dies ist "null" im Datenbanksinn "keinen Wert haben" im Gegensatz zum C++ NULL.)

Der Status `COleCurrency` eines Objekts ist in den folgenden Fällen ungültig:

- Wenn sein Wert von einem `COleVariant` VARIANT oder Wert festgelegt wird, der nicht in einen Währungswert konvertiert werden konnte.

- Wenn dieses Objekt während eines arithmetischen Zuweisungsvorgangs einen `+=` Über- oder Unterlauf erlebt hat, z. B. oder ** \* **.

- Wenn diesem Objekt ein ungültiger Wert zugewiesen wurde.

- Wenn der Status dieses Objekts mit [SetStatus](#setstatus)explizit auf ungültig festgelegt wurde.

Weitere Informationen zu Vorgängen, die den Status auf ungültig festlegen können, finden Sie in den folgenden Memberfunktionen:

- [COleCurrency](#colecurrency)

- [Operator =](#operator_eq)

- [Betreiber + -](#operator_plus_minus)

- [Operator += und -=](#operator_plus_minus_eq)

- [Bediener * /](#operator_star)

- [Operator *= und /=](#operator_star_div_eq)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

## <a name="colecurrencym_cur"></a><a name="m_cur"></a>COleCurrency::m_cur

Die zugrunde liegende `COleCurrency` [CURRENCY-Struktur](/windows/win32/api/wtypes/ns-wtypes-cy~r1) für dieses Objekt.

### <a name="remarks"></a>Bemerkungen

> [!CAUTION]
> Wenn Sie den `CURRENCY` Wert in der Struktur ändern, auf die `COleCurrency` der Zeiger, der von dieser Funktion zurückgegeben wird, zugegriffen wird, wird der Wert dieses Objekts geändert. Der Status dieses `COleCurrency` Objekts wird nicht geändert.

Weitere Informationen finden Sie im [CURRENCY-Eintrag](/windows/win32/api/wtypes/ns-wtypes-cy~r1) im Windows SDK.

## <a name="colecurrencym_status"></a><a name="m_status"></a>COleCurrency::m_status

Der Typ dieses Datenmembers ist der `CurrencyStatus`aufgezählte Typ `COleCurrency` , der innerhalb der Klasse definiert ist.

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>Bemerkungen

Eine kurze Beschreibung dieser Statuswerte finden Sie in der folgenden Liste:

- `COleCurrency::valid`Gibt an, dass dieses `COleCurrency` Objekt gültig ist.

- `COleCurrency::invalid`Gibt an, dass dieses `COleCurrency` Objekt ungültig ist. das heißt, sein Wert kann falsch sein.

- `COleCurrency::null`Gibt an, dass dieses `COleCurrency` Objekt null ist, d. h., dass kein Wert für dieses Objekt angegeben wurde. (Dies ist "null" im Datenbanksinn "keinen Wert haben" im Gegensatz zum C++ NULL.)

Der Status `COleCurrency` eines Objekts ist in den folgenden Fällen ungültig:

- Wenn sein Wert von einem `COleVariant` VARIANT oder Wert festgelegt wird, der nicht in einen Währungswert konvertiert werden konnte.

- Wenn dieses Objekt während eines arithmetischen Zuweisungsvorgangs einen `+=` Über- oder Unterlauf erlebt hat, z. B. oder ** \* **.

- Wenn diesem Objekt ein ungültiger Wert zugewiesen wurde.

- Wenn der Status dieses Objekts mit [SetStatus](#setstatus)explizit auf ungültig festgelegt wurde.

Weitere Informationen zu Vorgängen, die den Status auf ungültig festlegen können, finden Sie in den folgenden Memberfunktionen:

- [COleCurrency](#colecurrency)

- [Operator =](#operator_eq)

- [Betreiber +, -](#operator_plus_minus)

- [Operator +=, -=](#operator_plus_minus_eq)

- [Betreiber */](#operator_star)

- [Operator *=, /=](#operator_star_div_eq)

> [!CAUTION]
> Dieser Datenmember ist für fortgeschrittene Programmiersituationen. Sie sollten die Inline-Memberfunktionen [GetStatus](#getstatus) und [SetStatus](#setstatus)verwenden. Weitere `SetStatus` Hinweise zur expliziten Einstellung dieses Datenmembers finden Sie unter .

## <a name="colecurrencyoperator-"></a><a name="operator_eq"></a>COleCurrency::operator =

Diese überladenen Zuweisungsoperatoren kopieren `COleCurrency` den Quellwährungswert in dieses Objekt.

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>Bemerkungen

Eine kurze Beschreibung der einzelnen Operatoren folgt:

- **Operator =(** `cySrc` **)** Der `CURRENCY` Wert wird `COleCurrency` in das Objekt kopiert, und sein Status ist auf gültig festgelegt.

- **Operator =(** `curSrc` **)** Der Wert und Status des Operanden, ein vorhandenes `COleCurrency` Objekt wird in dieses `COleCurrency` Objekt kopiert.

- **Operator =(** *varSrc* **)** Wenn die Konvertierung `VARIANT` des Werts (oder [COleVariant-Objekts)](../../mfc/reference/colevariant-class.md) in eine Währung `VT_CY` `COleCurrency` ( ) erfolgreich ist, wird der konvertierte Wert in dieses Objekt kopiert und sein Status auf gültig festgelegt. Wenn die Konvertierung nicht erfolgreich ist, wird der Wert des `COleCurrency` Objekts auf 0 und sein Status auf ungültig gesetzt.

Weitere Informationen finden Sie in den Einträgen [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy~r1) und [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus"></a>COleCurrency::operator +, -

Mit diesen Operatoren können Sie `COleCurrency` zwei Werte zu und von einander `COleCurrency` hinzufügen und subtrahieren und das Vorzeichen eines Werts ändern.

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>Bemerkungen

Wenn einer der Operanden null ist, `COleCurrency` ist der Status des resultierenden Werts null.

Wenn der arithmetische Vorgang überläuft, ist der resultierende `COleCurrency` Wert ungültig.

Wenn der Operand ungültig ist und der andere nicht `COleCurrency` null ist, ist der Status des resultierenden Werts ungültig.

Weitere Informationen zu den gültigen, ungültigen und NULL-Statuswerten finden Sie in der m_status-Membervariablen. [m_status](#m_status)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus_eq"></a>COleCurrency::operator +=, -=

Ermöglicht das Hinzufügen und `COleCurrency` Subtrahieren `COleCurrency` eines Werts zu und von diesem Objekt.

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>Bemerkungen

Wenn einer der Operanden null ist, `COleCurrency` wird der Status dieses Objekts auf null gesetzt.

Wenn der arithmetische Vorgang überläuft, `COleCurrency` wird der Status dieses Objekts auf ungültig festgelegt.

Wenn einer der Operanden ungültig und der andere nicht null `COleCurrency` ist, wird der Status dieses Objekts auf ungültig gesetzt.

Weitere Informationen zu den gültigen, ungültigen und NULL-Statuswerten finden Sie in der m_status-Membervariablen. [m_status](#m_status)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

## <a name="colecurrencyoperator--and-"></a><a name="operator_star"></a>COleCurrency::operator \* und /

Ermöglicht es Ihnen, einen `COleCurrency` Wert um einen integralen Wert zu skalieren.

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>Bemerkungen

Wenn `COleCurrency` der Operand null ist, `COleCurrency` ist der Status des resultierenden Werts null.

Wenn der arithmetische Vorgang über- oder unterläuft, ist der Status des resultierenden `COleCurrency` Werts ungültig.

Wenn `COleCurrency` der Operand ungültig ist, ist `COleCurrency` der Status des resultierenden Werts ungültig.

Weitere Informationen zu den gültigen, ungültigen und NULL-Statuswerten finden Sie in der m_status-Membervariablen. [m_status](#m_status)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

## <a name="colecurrencyoperator--"></a><a name="operator_star_div_eq"></a>COleCurrency::operator \*=, /=

Ermöglicht es Ihnen, diesen `COleCurrency` Wert um einen integralen Wert zu skalieren.

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>Bemerkungen

Wenn `COleCurrency` der Operand null ist, `COleCurrency` wird der Status dieses Objekts auf null gesetzt.

Wenn der arithmetische Vorgang überläuft, `COleCurrency` wird der Status dieses Objekts auf ungültig festgelegt.

Wenn `COleCurrency` der Operand ungültig ist, `COleCurrency` wird der Status dieses Objekts auf ungültig gesetzt.

Weitere Informationen zu den gültigen, ungültigen und NULL-Statuswerten finden Sie in der m_status-Membervariablen. [m_status](#m_status)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

## <a name="colecurrencyoperator-ltlt-gtgt"></a><a name="operator_stream"></a>COleCurrency::operator &lt; &lt;,&gt;&gt;

Unterstützt Diagnose-Dumping und Speicherung in einem Archiv.

```
friend CDumpContext& operator<<(
    CDumpContext& dc,
    COleCurrency curSrc);

friend CArchive& operator<<(
    CArchive& ar,
    COleCurrency curSrc);

friend CArchive& operator>>(
    CArchive& ar,
    COleCurrency& curSrc);
```

### <a name="remarks"></a>Bemerkungen

Der Extraktionsoperator ( **>>**) unterstützt das Laden aus einem Archiv.

## <a name="colecurrencyoperator-currency"></a><a name="operator_currency"></a>COleCurrency::operator CURRENCY

Gibt `CURRENCY` eine Struktur zurück, `COleCurrency` deren Wert aus diesem Objekt kopiert wird.

```
operator CURRENCY() const;
```

### <a name="remarks"></a>Bemerkungen

## <a name="colecurrencyparsecurrency"></a><a name="parsecurrency"></a>COleCurrency::ParseWährung

Rufen Sie diese Memberfunktion auf, um eine Zeichenfolge zu analysieren, um einen Währungswert zu lesen.

```
BOOL ParseCurrency(
    LPCTSTR lpszCurrency,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT);

throw(CMemoryException*);
throw(COleException*);
```

### <a name="parameters"></a>Parameter

*lpszWährung*<br/>
Ein Zeiger auf die null-terminierte Zeichenfolge, die analysiert werden soll.

*dwFlags*<br/>
Zeigt Flags für Gebietsschemaeinstellungen an, möglicherweise das folgende Flag:

- LOCALE_NOUSEROVERRIDE Verwenden Sie die Standardgebietsschemaeinstellungen des Systems anstelle von benutzerdefinierten Benutzereinstellungen.

*Lcid*<br/>
Gibt die Gebietsschema-ID an, die für die Konvertierung verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Zeichenfolge erfolgreich in einen Währungswert konvertiert wurde, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Es verwendet lokale Sprachspezifikationen (Gebietsschema-IDs) für die Bedeutung nicht numerischer Zeichen in der Quellzeichenfolge.

Eine Erläuterung der Gebietsschema-ID-Werte finden Sie unter [Unterstützen mehrerer Sprachen](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages).

Wenn die Zeichenfolge erfolgreich in einen Währungswert `COleCurrency` konvertiert wurde, wird der Wert dieses Objekts auf diesen Wert und dessen Status auf gültig festgelegt.

Wenn die Zeichenfolge nicht in einen Währungswert konvertiert werden konnte oder ein `COleCurrency` numerischer Überlauf vorlag, ist der Status dieses Objekts ungültig.

Wenn die Zeichenfolgenkonvertierung aufgrund von Speicherzuweisungsfehlern fehlgeschlagen ist, löst diese Funktion eine [CMemoryException](../../mfc/reference/cmemoryexception-class.md)aus. In jedem anderen Fehlerzustand löst diese Funktion eine [COleException](../../mfc/reference/coleexception-class.md)aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

## <a name="colecurrency-relational-operators"></a><a name="colecurrency_relational_operators"></a>COleCurrency Relationale Operatoren

Vergleichen Sie zwei Währungswerte, und geben Sie einen Wert ungleich Null zurück, wenn die Bedingung wahr ist. andernfalls 0.

```
BOOL operator==(const COleCurrency& cur) const;
BOOL operator!=(const COleCurrency& cur) const;
BOOL operator<(const COleCurrency& cur) const;
BOOL operator>(const COleCurrency& cur) const;
BOOL operator<=(const COleCurrency& cur) const;
BOOL operator>=(const COleCurrency& cur) const;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Der Rückgabewert der Bestellvorgänge ** \< ** **>**( **>=** **<**, , , ) ist nicht definiert, wenn der Status von operand null oder ungültig ist. Die Gleichheitsoperatoren ( `==`, `!=`) berücksichtigen den Status der Operanden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

## <a name="colecurrencysetcurrency"></a><a name="setcurrency"></a>COleCurrency::SetCurrency

Rufen Sie diese Memberfunktion auf, um `COleCurrency` die Einheiten und den Bruchteil dieses Objekts festzulegen.

```cpp
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parameter

*nUnits*, *nFractionalUnits* Geben Sie die Einheiten und den Bruchteil (in 1/10.000) des Wertes an, der in dieses `COleCurrency` Objekt kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn der absolute Wert des Bruchteils größer als 10.000 ist, wird die entsprechende Anpassung an die Einheiten vorgenommen, wie in der dritten der folgenden Beispiele gezeigt.

Beachten Sie, dass die Einheiten und der Bruchteil durch signierte Long-Werte angegeben werden. Das vierte der folgenden Beispiele zeigt, was passiert, wenn die Parameter unterschiedliche Zeichen haben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

## <a name="colecurrencysetstatus"></a><a name="setstatus"></a>COleCurrency::SetStatus

Rufen Sie diese Memberfunktion auf, um `COleCurrency` den Status (Gültigkeit) dieses Objekts festzulegen.

```cpp
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>Parameter

*status*<br/>
Der neue Status `COleCurrency` für dieses Objekt.

### <a name="remarks"></a>Bemerkungen

Der *Statusparameterwert* wird `CurrencyStatus` durch den aufgezählten Typ definiert, der innerhalb der `COleCurrency` Klasse definiert ist.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Eine kurze Beschreibung dieser Statuswerte finden Sie in der folgenden Liste:

- `COleCurrency::valid`Gibt an, dass dieses `COleCurrency` Objekt gültig ist.

- `COleCurrency::invalid`Gibt an, dass dieses `COleCurrency` Objekt ungültig ist. das heißt, sein Wert kann falsch sein.

- `COleCurrency::null`Gibt an, dass dieses `COleCurrency` Objekt null ist, d. h., dass kein Wert für dieses Objekt angegeben wurde. (Dies ist "null" im Datenbanksinn "keinen Wert haben" im Gegensatz zum C++ NULL.)

> [!CAUTION]
> Diese Funktion ist für fortgeschrittene Programmiersituationen. Diese Funktion ändert die Daten in diesem Objekt nicht. Es wird am häufigsten verwendet, um den Status auf null oder ungültig festzulegen. Beachten Sie, dass der Zuweisungsoperator ( [operator =](#operator_eq)) und [SetCurrency](#setcurrency) den Status auf das Objekt basierend auf dem Quellwert(n) festlegen.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleVariant-Klasse](../../mfc/reference/colevariant-class.md)
