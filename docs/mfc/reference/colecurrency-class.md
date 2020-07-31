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
ms.openlocfilehash: ced4554701cef5fd6f790b9e37f4c1b41746b1ad
ms.sourcegitcommit: 13f42c339fb7af935e3a93ac80e350d5e784c9f1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2020
ms.locfileid: "87470965"
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
|[COleCurrency:: COleCurrency](#colecurrency)|Erstellt ein `COleCurrency`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[COleCurrency:: Format](#format)|Generiert eine formatierte Zeichen folgen Darstellung eines- `COleCurrency` Objekts.|
|[COleCurrency:: GetStatus](#getstatus)|Ruft den Status (Gültigkeit) dieses- `COleCurrency` Objekts ab.|
|[COleCurrency::P arsecurrency](#parsecurrency)|Liest einen Currency-Wert aus einer Zeichenfolge und legt den Wert von fest `COleCurrency` .|
|[COleCurrency:: setCurrency](#setcurrency)|Legt den Wert dieses- `COleCurrency` Objekts fest.|
|[COleCurrency:: SetStatus](#setstatus)|Legt den Status (Gültigkeit) für dieses- `COleCurrency` Objekt fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Operator =](#operator_eq)|Kopiert einen `COleCurrency` Wert.|
|[Operator +,-](#operator_plus_minus)|Fügt ein Vorzeichen von Werten hinzu, subtrahiert und ändert Sie `COleCurrency` .|
|[Operator + =,-=](#operator_plus_minus_eq)|Fügt einen Wert von diesem-Objekt hinzu und subtrahiert `COleCurrency` diesen `COleCurrency` .|
|[Operator */](#operator_star)|Skaliert einen `COleCurrency` Wert mit einem ganzzahligen Wert.|
|[Operator * =,/=](#operator_star_div_eq)|Skaliert diesen `COleCurrency` Wert um einen ganzzahligen Wert.|
|[Operator <<](#operator_stream)|Gibt einen `COleCurrency` Wert in `CArchive` oder aus `CDumpContext` .|
|[Operator >>](#operator_stream)|Gibt ein- `COleCurrency` Objekt aus `CArchive` .|
|[Operator Währung](#operator_currency)|Konvertiert einen `COleCurrency` Wert in eine Währung.|
|[Operator = =, <, <= usw.](#colecurrency_relational_operators)|Vergleicht zwei `COleCurrency` Werte.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleCurrency:: m_cur](#m_cur)|Enthält die zugrunde liegende Währung für dieses `COleCurrency` Objekt.|
|[COleCurrency:: m_status](#m_status)|Enthält den Status dieses `COleCurrency` Objekts.|

## <a name="remarks"></a>Hinweise

`COleCurrency`weist keine Basisklasse auf.

Währung wird als 8-Byte-Ganzzahl mit zwei Komplement Werten implementiert, die von 10.000 skaliert wird. Dies ermöglicht eine Festkommazahl mit 15 Stellen links vom Dezimaltrennzeichen und 4 Ziffern rechts. Der Currency-Datentyp ist äußerst nützlich für Berechnungen, die Geld betreffen, oder für eine beliebige fest Punkt Berechnung, bei der die Genauigkeit wichtig ist. Dies ist einer der möglichen Typen für den `VARIANT` Datentyp der OLE-Automatisierung.

`COleCurrency`implementiert außerdem einige grundlegende arithmetische Operationen für diesen festpunkttyp. Die unterstützten Vorgänge wurden ausgewählt, um die Rundungsfehler zu steuern, die während der festgelegten Berechnung auftreten.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`COleCurrency`

## <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="colecurrencycolecurrency"></a><a name="colecurrency"></a>COleCurrency:: COleCurrency

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

*cysrc*<br/>
Ein Währungswert, der in das neue-Objekt kopiert werden soll `COleCurrency` .

*Cursor*<br/>
Ein vorhandenes- `COleCurrency` Objekt, das in das neue-Objekt kopiert werden soll `COleCurrency` .

*varSrc*<br/>
Eine vorhandene `VARIANT` Datenstruktur (möglicherweise ein- `COleVariant` Objekt), die in einen Währungswert (VT_CY) konvertiert und in das neue-Objekt kopiert werden soll `COleCurrency` .

*nunits*, *nfractionalunits* , gibt die Einheiten und den Bruchteil (in 1/10000) des Werts an, der in das neue-Objekt kopiert werden soll `COleCurrency` .

### <a name="remarks"></a>Hinweise

Alle diese Konstruktoren erstellen neue `COleCurrency` Objekte, die mit dem angegebenen Wert initialisiert werden. Eine kurze Beschreibung der einzelnen Konstruktoren folgt. Sofern nicht anders angegeben, wird der Status des neuen `COleCurrency` Elements auf gültig festgelegt.

- COleCurrency () erstellt ein- `COleCurrency` Objekt, das mit 0 (null) initialisiert wird.

- COleCurrency ( `cySrc` ) erstellt ein- `COleCurrency` Objekt aus einem [Währungs](/windows/win32/api/wtypes/ns-wtypes-cy-r1) Wert.

- COleCurrency ( `curSrc` ) erstellt ein- `COleCurrency` Objekt aus einem vorhandenen- `COleCurrency` Objekt. Das neue-Objekt hat denselben Status wie das Quell Objekt.

- COleCurrency ( `varSrc` ) erstellt ein- `COleCurrency` Objekt. Versucht, eine VARIANT-Struktur oder ein [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) - `COleVariant` Objekt in einen Currency-Wert (VT_CY) zu konvertieren. Wenn diese Konvertierung erfolgreich ist, wird der konvertierte Wert in das neue- `COleCurrency` Objekt kopiert. Wenn dies nicht der Fall ist, wird der Wert des `COleCurrency` -Objekts auf NULL (0) und seinen Status auf ungültig festgelegt.

- COleCurrency ( `nUnits` , `nFractionalUnits` ) erstellt ein- `COleCurrency` Objekt aus den angegebenen numerischen Komponenten. Wenn der absolute Wert des Bruchteils größer als 10.000 ist, wird die entsprechende Anpassung an den Einheiten vorgenommen. Beachten Sie, dass die Einheiten und die Bruchteile durch signierte Long-Werte angegeben werden.

Weitere Informationen finden Sie in den [Währungs](/windows/win32/api/wtypes/ns-wtypes-cy-r1) -und [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) -Einträgen in der Windows SDK.

### <a name="example"></a>Beispiel

In den folgenden Beispielen werden die Auswirkungen des NULL-Parameters und der Konstruktoren mit zwei Parameterwerten veranschaulicht:

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

## <a name="colecurrencyformat"></a><a name="format"></a>COleCurrency:: Format

Rufen Sie diese Member-Funktion auf, um eine formatierte Darstellung des Währungs Werts zu erstellen.

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
Gibt Flags für Gebiets Schema Einstellungen an. Nur das folgende Flag ist für die Währung relevant:

- LOCALE_NOUSEROVERRIDE die Standardeinstellungen des System Gebiets Schemas anstelle von benutzerdefinierten Benutzereinstellungen verwenden.

*lcid*<br/>
Gibt die für die Konvertierung zu verwendende Gebiets Schema-ID an.

### <a name="return-value"></a>Rückgabewert

Ein- `CString` Wert, der den formatierten Währungswert enthält.

### <a name="remarks"></a>Hinweise

Der Wert wird mit den Spezifikationen der lokalen Sprache (Gebiets Schema-IDs) formatiert. Ein Währungssymbol ist nicht im zurückgegebenen Wert enthalten. Wenn der Status dieses `COleCurrency` Objekts NULL ist, ist der Rückgabewert eine leere Zeichenfolge. Wenn der Status ungültig ist, wird die Rückgabe Zeichenfolge durch die IDS_INVALID_CURRENCY der Zeichen folgen Ressource angegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

## <a name="colecurrencygetstatus"></a><a name="getstatus"></a>COleCurrency:: GetStatus

Mit dieser Member-Funktion können Sie den Status (Gültigkeit) eines bestimmten `COleCurrency` Objekts abrufen.

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt den Status dieses `COleCurrency` Werts zurück.

### <a name="remarks"></a>Hinweise

Der Rückgabewert wird durch den `CurrencyStatus` Enumerationstyp definiert, der in der-Klasse definiert ist `COleCurrency` .

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Eine kurze Beschreibung dieser Statuswerte finden Sie in der folgenden Liste:

- `COleCurrency::valid`Gibt an, dass dieses- `COleCurrency` Objekt gültig ist.

- `COleCurrency::invalid`Gibt an, dass dieses- `COleCurrency` Objekt ungültig ist, d. h., sein Wert ist möglicherweise falsch.

- `COleCurrency::null`Gibt an, dass dieses `COleCurrency` Objekt NULL ist, d. h., es wurde kein Wert für dieses Objekt angegeben. (Dies ist "Null", wenn kein Wert vorhanden ist, und nicht der C++ NULL.)

Der Status eines- `COleCurrency` Objekts ist in den folgenden Fällen ungültig:

- , Wenn der Wert von einem Variant-oder-Wert festgelegt wird `COleVariant` , der nicht in einen Währungswert konvertiert werden konnte.

- , Wenn bei einem arithmetischen Zuweisungs Vorgang für dieses Objekt ein Überlauf oder Unterlauf aufgetreten ist, z `+=` **\*=** . b. oder.

- , Wenn diesem Objekt ein ungültiger Wert zugewiesen wurde.

- , Wenn der Status dieses Objekts mithilfe von [SetStatus](#setstatus)explizit auf ungültig festgelegt wurde.

Weitere Informationen zu Vorgängen, die den Status als ungültig festlegen können, finden Sie in den folgenden Element Funktionen:

- [COleCurrency](#colecurrency)

- [Operator =](#operator_eq)

- [Operator +-](#operator_plus_minus)

- [Operator + = und-=](#operator_plus_minus_eq)

- [Operator */](#operator_star)

- [Operator * = und/=](#operator_star_div_eq)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

## <a name="colecurrencym_cur"></a><a name="m_cur"></a>COleCurrency:: m_cur

Die zugrunde liegende [Währungs](/windows/win32/api/wtypes/ns-wtypes-cy-r1) Struktur für dieses- `COleCurrency` Objekt.

### <a name="remarks"></a>Hinweise

> [!CAUTION]
> Wenn Sie den Wert in der Struktur ändern, auf `CURRENCY` die der von dieser Funktion zurückgegebene Zeiger zugreift, wird der Wert dieses `COleCurrency` Objekts geändert. Der Status dieses Objekts wird nicht geändert `COleCurrency` .

Weitere Informationen finden Sie im [Währungs](/windows/win32/api/wtypes/ns-wtypes-cy-r1) Eintrag in der Windows SDK.

## <a name="colecurrencym_status"></a><a name="m_status"></a>COleCurrency:: m_status

Der Typ dieses Datenmembers ist der Enumerationstyp `CurrencyStatus` , der in der-Klasse definiert ist `COleCurrency` .

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>Hinweise

Eine kurze Beschreibung dieser Statuswerte finden Sie in der folgenden Liste:

- `COleCurrency::valid`Gibt an, dass dieses- `COleCurrency` Objekt gültig ist.

- `COleCurrency::invalid`Gibt an, dass dieses- `COleCurrency` Objekt ungültig ist, d. h., sein Wert ist möglicherweise falsch.

- `COleCurrency::null`Gibt an, dass dieses `COleCurrency` Objekt NULL ist, d. h., es wurde kein Wert für dieses Objekt angegeben. (Dies ist "Null", wenn kein Wert vorhanden ist, und nicht der C++ NULL.)

Der Status eines- `COleCurrency` Objekts ist in den folgenden Fällen ungültig:

- , Wenn der Wert von einem Variant-oder-Wert festgelegt wird `COleVariant` , der nicht in einen Währungswert konvertiert werden konnte.

- , Wenn bei einem arithmetischen Zuweisungs Vorgang für dieses Objekt ein Überlauf oder Unterlauf aufgetreten ist, z `+=` **\*=** . b. oder.

- , Wenn diesem Objekt ein ungültiger Wert zugewiesen wurde.

- , Wenn der Status dieses Objekts mithilfe von [SetStatus](#setstatus)explizit auf ungültig festgelegt wurde.

Weitere Informationen zu Vorgängen, die den Status als ungültig festlegen können, finden Sie in den folgenden Element Funktionen:

- [COleCurrency](#colecurrency)

- [Operator =](#operator_eq)

- [Operator +,-](#operator_plus_minus)

- [Operator + =,-=](#operator_plus_minus_eq)

- [Operator */](#operator_star)

- [Operator * =,/=](#operator_star_div_eq)

> [!CAUTION]
> Dieser Datenmember ist für erweiterte Programmier Situationen vorgesehen. Sie sollten die Inline Member-Funktionen [GetStatus](#getstatus) und [SetStatus](#setstatus)verwenden. `SetStatus`Weitere Vorsichtsmaßnahmen bezüglich der expliziten Festlegung dieses Datenmembers finden Sie unter.

## <a name="colecurrencyoperator-"></a><a name="operator_eq"></a>COleCurrency:: Operator =

Diese überladenen Zuweisungs Operatoren kopieren den Wert der Quell Währung in dieses `COleCurrency` Objekt.

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>Hinweise

Eine kurze Beschreibung der einzelnen Operatoren folgt:

- **Operator = (** `cySrc` **)** der `CURRENCY` Wert wird in das `COleCurrency` -Objekt kopiert, und sein Status ist auf "valid" festgelegt.

- **Operator = (** `curSrc` **)** der Wert und der Status des Operanden, ein vorhandenes `COleCurrency` Objekt wird in dieses `COleCurrency` Objekt kopiert.

- **Operator = (** *varSrc* **)** Wenn die Konvertierung des `VARIANT` Werts (oder des [COleVariant](../../mfc/reference/colevariant-class.md) -Objekts) in eine Währung ( `VT_CY` ) erfolgreich ist, wird der konvertierte Wert in dieses `COleCurrency` Objekt kopiert und sein Status auf "gültig" festgelegt. Wenn die Konvertierung nicht erfolgreich ist, wird der Wert des `COleCurrency` -Objekts auf 0 und dessen Status auf ungültig festgelegt.

Weitere Informationen finden Sie in den [Währungs](/windows/win32/api/wtypes/ns-wtypes-cy-r1) -und [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) -Einträgen in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus"></a>COleCurrency:: Operator +,-

Mit diesen Operatoren können Sie zwei Werte zu und voneinander subtrahieren und `COleCurrency` das Vorzeichen eines `COleCurrency` Werts ändern.

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>Hinweise

Wenn einer der Operanden NULL ist, ist der Status des resultierenden `COleCurrency` Werts Null.

Bei einem Überlauf der arithmetischen Operation ist der resultierende `COleCurrency` Wert ungültig.

Wenn der Operand ungültig ist und der andere nicht NULL ist, ist der Status des resultierenden `COleCurrency` Werts ungültig.

Weitere Informationen zu den gültigen, ungültigen und NULL-Status Werten finden Sie in der [m_status](#m_status) Member-Variable.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus_eq"></a>COleCurrency:: Operator + =,-=

Ermöglicht das Hinzufügen und Subtrahieren eines `COleCurrency` Werts zu und von diesem `COleCurrency` Objekt.

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>Hinweise

Wenn einer der Operanden NULL ist, wird der Status dieses `COleCurrency` Objekts auf NULL festgelegt.

Bei einem Überlauf der arithmetischen Operation wird der Status dieses `COleCurrency` Objekts auf ungültig festgelegt.

Wenn einer der Operanden ungültig ist und der andere nicht NULL ist, wird der Status dieses `COleCurrency` Objekts auf ungültig festgelegt.

Weitere Informationen zu den gültigen, ungültigen und NULL-Status Werten finden Sie in der [m_status](#m_status) Member-Variable.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

## <a name="colecurrencyoperator--and-"></a><a name="operator_star"></a>COleCurrency:: \* -Operator und/

Ermöglicht das Skalieren eines `COleCurrency` Werts durch einen ganzzahligen Wert.

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>Hinweise

Wenn der `COleCurrency` Operand NULL ist, ist der Status des resultierenden `COleCurrency` Werts Null.

Wenn bei der arithmetischen Operation ein Überlauf oder Unterlauf erfolgt, ist der Status des resultierenden `COleCurrency` Werts ungültig.

Wenn der `COleCurrency` Operand ungültig ist, ist der Status des resultierenden `COleCurrency` Werts ungültig.

Weitere Informationen zu den gültigen, ungültigen und NULL-Status Werten finden Sie in der [m_status](#m_status) Member-Variable.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

## <a name="colecurrencyoperator--"></a><a name="operator_star_div_eq"></a>COleCurrency:: Operator \* =,/=

Ermöglicht das Skalieren dieses `COleCurrency` Werts durch einen ganzzahligen Wert.

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>Hinweise

Wenn der `COleCurrency` Operand NULL ist, wird der Status dieses `COleCurrency` Objekts auf NULL festgelegt.

Bei einem Überlauf der arithmetischen Operation wird der Status dieses `COleCurrency` Objekts auf ungültig festgelegt.

Wenn der `COleCurrency` Operand ungültig ist, wird der Status dieses `COleCurrency` Objekts auf ungültig festgelegt.

Weitere Informationen zu den gültigen, ungültigen und NULL-Status Werten finden Sie in der [m_status](#m_status) Member-Variable.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

## <a name="colecurrencyoperator-ltlt-gtgt"></a><a name="operator_stream"></a>COleCurrency::-Operator &lt; &lt; ,&gt;&gt;

Unterstützt das Ausgeben von Diagnosen und das Speichern in einem Archiv.

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

### <a name="remarks"></a>Hinweise

Der Extraktions **>>** Operator () unterstützt das Laden aus einem Archiv.

## <a name="colecurrencyoperator-currency"></a><a name="operator_currency"></a>COleCurrency:: Operator Währung

Gibt eine-Struktur zurück, `CURRENCY` deren Wert aus diesem-Objekt kopiert wird `COleCurrency` .

```
operator CURRENCY() const;
```

### <a name="remarks"></a>Hinweise

## <a name="colecurrencyparsecurrency"></a><a name="parsecurrency"></a>COleCurrency::P arsecurrency

Mit dieser Member-Funktion können Sie eine Zeichenfolge analysieren, um einen Währungswert zu lesen.

```
BOOL ParseCurrency(
    LPCTSTR lpszCurrency,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT);

throw(CMemoryException*);
throw(COleException*);
```

### <a name="parameters"></a>Parameter

*lpszcurrency*<br/>
Ein Zeiger auf die mit NULL endende Zeichenfolge, die analysiert werden soll.

*dwFlags*<br/>
Gibt Flags für Gebiets Schema Einstellungen an, möglicherweise das folgende Flag:

- LOCALE_NOUSEROVERRIDE die Standardeinstellungen des System Gebiets Schemas anstelle von benutzerdefinierten Benutzereinstellungen verwenden.

*lcid*<br/>
Gibt die für die Konvertierung zu verwendende Gebiets Schema-ID an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn die Zeichenfolge erfolgreich in einen Währungswert konvertiert wurde, andernfalls 0.

### <a name="remarks"></a>Hinweise

Dabei werden lokale Sprachspezifikationen (Gebiets Schema-IDs) für die Bedeutung von nicht numerischen Zeichen in der Quell Zeichenfolge verwendet.

Eine Erläuterung der Werte für die Gebiets Schema-ID finden Sie [unter Unterstützung mehrerer Sprachen](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages).

Wenn die Zeichenfolge erfolgreich in einen Währungswert konvertiert wurde, wird der Wert dieses `COleCurrency` Objekts auf diesen Wert und seinen Status auf gültig festgelegt.

Wenn die Zeichenfolge nicht in einen Währungswert konvertiert werden konnte oder ein numerischer Überlauf aufgetreten ist, ist der Status dieses `COleCurrency` Objekts ungültig.

Wenn die Zeichen folgen Konvertierung aufgrund von Speicher Belegungs Fehlern fehlgeschlagen ist, löst diese Funktion eine [cmemoryexception](../../mfc/reference/cmemoryexception-class.md)aus. In jedem anderen Fehlerzustand löst diese Funktion eine [COleException](../../mfc/reference/coleexception-class.md)aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

## <a name="colecurrency-relational-operators"></a><a name="colecurrency_relational_operators"></a>Relationale COleCurrency-Operatoren

Vergleicht zwei Währungswerte und gibt einen Wert ungleich 0 (null) zurück, wenn die Bedingung zutrifft. andernfalls 0.

```
BOOL operator==(const COleCurrency& cur) const;
BOOL operator!=(const COleCurrency& cur) const;
BOOL operator<(const COleCurrency& cur) const;
BOOL operator>(const COleCurrency& cur) const;
BOOL operator<=(const COleCurrency& cur) const;
BOOL operator>=(const COleCurrency& cur) const;
```

### <a name="remarks"></a>Hinweise

> [!NOTE]
> Der Rückgabewert der Reihenfolge Vorgänge ( **<** , **\<=**, **>** , **>=** ) ist nicht definiert, wenn der Status eines der beiden Operanden NULL oder ungültig ist. Die Gleichheits Operatoren ( `==` , `!=` ) überprüfen den Status der Operanden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

## <a name="colecurrencysetcurrency"></a><a name="setcurrency"></a>COleCurrency:: setCurrency

Mit dieser Member-Funktion legen Sie die Einheiten und den Bruch Teil dieses `COleCurrency` Objekts fest.

```cpp
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parameter

*nunits*, *nfractionalunits* , gibt die Einheiten und den Bruchteil (in 1/10000) des Werts an, der in dieses Objekt kopiert werden soll `COleCurrency` .

### <a name="remarks"></a>Hinweise

Wenn der absolute Wert des Bruchteils größer als 10.000 ist, wird die entsprechende Anpassung an die Einheiten vorgenommen, wie in den folgenden Beispielen gezeigt.

Beachten Sie, dass die Einheiten und die Bruchteile durch signierte Long-Werte angegeben werden. Das vierte der folgenden Beispiele zeigt, was geschieht, wenn die Parameter unterschiedliche Zeichen aufweisen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

## <a name="colecurrencysetstatus"></a><a name="setstatus"></a>COleCurrency:: SetStatus

Mit dieser Member-Funktion können Sie den Status (Gültigkeit) dieses `COleCurrency` Objekts festlegen.

```cpp
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>Parameter

*status*<br/>
Der neue Status für dieses `COleCurrency` Objekt.

### <a name="remarks"></a>Hinweise

Der *Status* Parameterwert wird durch den `CurrencyStatus` enumerierten Typ definiert, der in der- `COleCurrency` Klasse definiert ist.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Eine kurze Beschreibung dieser Statuswerte finden Sie in der folgenden Liste:

- `COleCurrency::valid`Gibt an, dass dieses- `COleCurrency` Objekt gültig ist.

- `COleCurrency::invalid`Gibt an, dass dieses- `COleCurrency` Objekt ungültig ist, d. h., sein Wert ist möglicherweise falsch.

- `COleCurrency::null`Gibt an, dass dieses `COleCurrency` Objekt NULL ist, d. h., es wurde kein Wert für dieses Objekt angegeben. (Dies ist "Null", wenn kein Wert vorhanden ist, und nicht der C++ NULL.)

> [!CAUTION]
> Diese Funktion ist für erweiterte Programmier Situationen vorgesehen. Diese Funktion ändert nicht die Daten in diesem-Objekt. Es wird am häufigsten verwendet, um den Status auf NULL oder ungültig festzulegen. Beachten Sie, dass der Zuweisungs Operator ( [Operator =](#operator_eq)) und [setCurrency](#setcurrency) den Status des Objekts auf der Grundlage der Quell Werte festlegen.

## <a name="see-also"></a>Siehe auch

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[COleVariant-Klasse](../../mfc/reference/colevariant-class.md)
