---
title: CComCurrency-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComCurrency
- ATLCUR/ATL::CComCurrency
- ATLCUR/ATL::CComCurrency::CComCurrency
- ATLCUR/ATL::CComCurrency::GetCurrencyPtr
- ATLCUR/ATL::CComCurrency::GetFraction
- ATLCUR/ATL::CComCurrency::GetInteger
- ATLCUR/ATL::CComCurrency::Round
- ATLCUR/ATL::CComCurrency::SetFraction
- ATLCUR/ATL::CComCurrency::SetInteger
- ATLCUR/ATL::CComCurrency::m_currency
helpviewer_keywords:
- CComCurrency class
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
ms.openlocfilehash: 541944e03e9caf6cba15612cf9e7cbbd239555ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327944"
---
# <a name="ccomcurrency-class"></a>CComCurrency-Klasse

`CComCurrency` verfügt über Methoden und Operatoren zum Erstellen und Verwalten eines CURRENCY-Objekts.

## <a name="syntax"></a>Syntax

```
class CComCurrency
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCurrency::CComCurrency](#ccomcurrency)|Der Konstruktor für ein `CComCurrency`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|Gibt die Adresse eines `m_currency`-Datenmembers zurück.|
|[CComCurrency::GetFraction](#getfraction)|Rufen Sie diese Methode auf, um den Nachkommawert eines `CComCurrency`-Objekts zurückzugeben.|
|[CComCurrency::GetInteger](#getinteger)|Rufen Sie diese Methode auf, um die ganzzahlige Komponente eines `CComCurrency`-Objekts zurückzugeben.|
|[CComCurrency::Round](#round)|Rufen Sie diese Methode auf, um ein `CComCurrency`-Objekt auf den nächsten ganzzahligen Wert zu runden.|
|[CComCurrency::SetFraction](#setfraction)|Rufen Sie diese Methode auf, um den Nachkommawert eines `CComCurrency`-Objekts festzulegen.|
|[CComCurrency::SetInteger](#setinteger)|Rufen Sie diese Methode auf, um den ganzzahligen Wert eines `CComCurrency`-Objekts festzulegen.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCurrency::operator -](#operator_-)|Dieser Operator wird verwendet, um Subtraktion für ein `CComCurrency`-Objekt auszuführen.|
|[CComCurrency::operator !=](#operator_neq)|Überprüft zwei `CComCurrency`-Objekte auf Ungleichheit.|
|[CComCurrency::Operator *](#operator_star)|Dieser Operator wird verwendet, um Multiplikation für ein `CComCurrency`-Objekt auszuführen.|
|[CComCurrency::operator *=](#operator_star_eq)|Dieser Operator wird verwendet, um Multiplikation für ein `CComCurrency`-Objekt auszuführen und ihm das Ergebnis zuzuweisen.|
|[CComCurrency::operator /](#operator_div)|Dieser Operator wird verwendet, um Division für ein `CComCurrency`-Objekt auszuführen.|
|[CComCurrency::operator /=](#operator_div_eq)|Dieser Operator wird verwendet, um Division für ein `CComCurrency`-Objekt auszuführen und ihm das Ergebnis zuzuweisen.|
|[CComCurrency::Operator +](#operator_add)|Dieser Operator wird verwendet, um Addition für ein `CComCurrency`-Objekt auszuführen.|
|[CComCurrency::operator +=](#operator_add_eq)|Dieser Operator wird verwendet, um Addition für ein `CComCurrency`-Objekt auszuführen und das Ergebnis dem aktuellen Objekt zuzuweisen.|
|[CComCurrency::operator <](#operator_lt)|Dieser Operator vergleicht zwei `CComCurrency`-Objekte, um das kleinere zu bestimmen.|
|[CComCurrency::operator <=](#operator_lt_eq)|Dieser Operator vergleicht zwei `CComCurrency`-Objekte, um zu bestimmen, ob sie gleich sind oder welches kleiner ist.|
|[CComCurrency::operator =](#operator_eq)|Dieser Operator weist dem `CComCurrency`-Objekt einen neuen Wert zu.|
|[CComCurrency::operator -=](#operator_-_eq)|Dieser Operator wird verwendet, um Subtraktion für ein `CComCurrency`-Objekt auszuführen und ihm das Ergebnis zuzuweisen.|
|[CComCurrency::operator ==](#operator_eq_eq)|Dieser Operator überprüft zwei `CComCurrency`-Objekte auf Gleichheit.|
|[CComCurrency::operator >](#operator_gt)|Dieser Operator vergleicht zwei `CComCurrency`-Objekte, um das größere zu bestimmen.|
|[CComCurrency::operator >=](#operator_gt_eq)|Dieser Operator vergleicht zwei `CComCurrency`-Objekte, um zu bestimmen, ob sie gleich sind oder welches größer ist.|
|[CComCurrency::operator CURRENCY](#operator_currency)|Gibt ein CURRENCY-Objekt um.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCurrency::m_currency](#m_currency)|Die CURRENCY-Variable, die von Ihrer Klasseninstanz erstellt wurde.|

## <a name="remarks"></a>Bemerkungen

`CComCurrency` ist ein Wrapper für den CURRENCY-Datentyp. CURRENCY ist als ganzzahliger 8-Byte-Zweierkomplementwert, skaliert mit 10.000, implementiert. Dies ermöglicht eine Festkommazahl mit 15 Stellen links vom Dezimaltrennzeichen und 4 Ziffern rechts. Der Datentyp CURRENCY ist äußerst nützlich für Finanzberechnungen oder für Festkommaberechnungen, bei denen Genauigkeit wichtig ist.

Der `CComCurrency` Wrapper implementiert Arithmetik-, Zuweisungs- und Vergleichsvorgänge für diesen Festpunkttyp. Die unterstützten Anwendungen wurden ausgewählt, um die Rundungsfehler zu steuern, die während der Festkommaberechnungen auftreten können.

Das `CComCurrency`-Objekt bietet Zugriff auf die Zahlen auf beiden Seiten des Dezimaltrennzeichens in der Form von zwei Komponenten: eine Ganzzahlkomponente, die den Wert links vom Dezimalzeichen speichert, und eine Nachkommakomponente, die den Wert rechts vom Dezimalzeichen speichert. Der Nachkommawert wird intern als eine ganze Zahl zwischen -9999 (CY_MIN_FRACTION) und +9999 (CY_MAX_FRACTION) gespeichert. Die Methode [CComCurrency::GetFraction](#getfraction) gibt einen Wert zurück, der um den Faktor 10000 (CY_SCALE) skaliert wird.

Beachten Sie beim Angeben der ganzzahligen `CComCurrency` und fraktionierten Komponenten eines Objekts, dass die Bruchkomponente eine Zahl im Bereich 0 bis 9999 ist. Dies ist bei einer Währung wie z. B. dem US-Dollar wichtig, bei der die Summen nur mit zwei signifikante Ziffern nach dem Dezimaltrennzeichen ausgedrückt werden. Obwohl die letzten zwei Ziffern nicht angezeigt werden, müssen sie berücksichtigt werden.

|Wert|Mögliche CComCurrency-Zuweisungen|
|-----------|---------------------------------------|
|$10.50|CComCurrency(10,5000) *oder* CComCurrency(10.50)|
|$10.05|CComCurrency(10.500) *oder* CComCurrency(10.05)|

Die Werte CY_MIN_FRACTION, CY_MAX_FRACTION und CY_SCALE sind in „atlcur.h“ definiert.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcur.h

## <a name="ccomcurrencyccomcurrency"></a><a name="ccomcurrency"></a>CComCurrency::CComCurrency

Der Konstruktor.

```
CComCurrency() throw();
CComCurrency(const CComCurrency& curSrc) throw();
CComCurrency(CURRENCY cySrc) throw();
CComCurrency(DECIMAL dSrc);
CComCurrency(ULONG ulSrc);
CComCurrency(USHORT usSrc);
CComCurrency(CHAR cSrc);
CComCurrency(DOUBLE dSrc);
CComCurrency(FLOAT fSrc);
CComCurrency(LONG lSrc);
CComCurrency(SHORT sSrc);
CComCurrency(BYTE bSrc);
CComCurrency(LONGLONG nInteger, SHORT nFraction);
explicit CComCurrency(LPDISPATCH pDispSrc);
explicit CComCurrency(const VARIANT& varSrc);
explicit CComCurrency(LPCWSTR szSrc);
explicit CComCurrency(LPCSTR szSrc);
```

### <a name="parameters"></a>Parameter

*curSrc*<br/>
Ein vorhandenes `CComCurrency`-Objekt.

*cySrc*<br/>
Eine Variable vom Typ CURRENCY.

*bSrc*, *dSrc*, *fSrc*, *lSrc*, *sSrc*, *ulSrc , usSrc*<br/>
Der Anfangswert, der `m_currency`der Membervariablen zugewiesen wurde.

*Csrc*<br/>
Ein Zeichen, das den Anfangswert `m_currency`der Membervariablen enthält.

*nInteger*, *nFraktion*<br/>
Die ganzzahligen und fraktionierten Komponenten des ursprünglichen monetären Werts. Weitere Informationen finden Sie in der [CComCurrency-Übersicht.](../../atl/reference/ccomcurrency-class.md)

*pDispSrc*<br/>
Ein `IDispatch` Zeiger.

*varSrc*<br/>
Eine Variable vom Typ VARIANT. Das Gebietsschema des aktuellen Threads wird zum Durchführen der Konvertierung verwendet.

*szSrc*<br/>
Eine Unicode- oder ANSI-Zeichenfolge, die den Anfangswert enthält. Das Gebietsschema des aktuellen Threads wird zum Durchführen der Konvertierung verwendet.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor legt den Anfangswert von [CComCurrency::m_currency](#m_currency)fest und akzeptiert eine Vielzahl von Datentypen, einschließlich Ganzzahlen, Zeichenfolgen, Gleitkommanummern, CURRENCY-Variablen und anderen `CComCurrency` Objekten. Wenn kein Wert `m_currency` angegeben wird, wird auf 0 gesetzt.

Im Falle eines Fehlers, z. B. eines Überlaufs, fehlen die Konstruktoren eine leere Ausnahmespezifikation (**throw()**) mit `AtlThrow` einem HRESULT, der den Fehler beschreibt.

Wenn Sie Gleitkomma- oder Doppelwerte `CComCurrency(10.50)` zum Zuweisen `CComCurrency(10,5000)` eines `CComCurrency(10,50)`Werts verwenden, beachten Sie eine Notiz, die der wertäquivalent ist und nicht .

## <a name="ccomcurrencygetcurrencyptr"></a><a name="getcurrencyptr"></a>CComCurrency::GetCurrencyPtr

Gibt die Adresse eines `m_currency`-Datenmembers zurück.

```
CURRENCY* GetCurrencyPtr() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Adresse `m_currency` eines Datenelements zurück

## <a name="ccomcurrencygetfraction"></a><a name="getfraction"></a>CComCurrency::GetFraction

Rufen Sie diese Methode auf, `CComCurrency` um die Bruchkomponente des Objekts zurückzugeben.

```
SHORT GetFraction() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Bruchkomponente `m_currency` des Datenelements zurück.

### <a name="remarks"></a>Bemerkungen

Die Bruchkomponente ist ein 4-stelliger Ganzzahlwert zwischen -9999 (CY_MIN_FRACTION) und +9999 (CY_MAX_FRACTION). `GetFraction`gibt diesen Wert um 10000 (CY_SCALE) zurück. Die Werte CY_MIN_FRACTION, CY_MAX_FRACTION und CY_SCALE werden in atlcur.h definiert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]

## <a name="ccomcurrencygetinteger"></a><a name="getinteger"></a>CComCurrency::GetInteger

Rufen Sie diese Methode auf, um `CComCurrency` die ganzzahlige Komponente eines Objekts abzurufen.

```
LONGLONG GetInteger() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die ganzzahlige `m_currency` Komponente des Datenelements zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]

## <a name="ccomcurrencym_currency"></a><a name="m_currency"></a>CComCurrency::m_currency

Das CURRENCY-Datenelement.

```
CURRENCY m_currency;
```

### <a name="remarks"></a>Bemerkungen

Dieser Member enthält die Währung, auf die mit den Methoden dieser Klasse zugegriffen und diese manipuliert werden kann.

## <a name="ccomcurrencyoperator--"></a><a name="operator_-"></a>CComCurrency::operator -

Dieser Operator wird verwendet, um Subtraktion für ein `CComCurrency`-Objekt auszuführen.

```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parameter

*Cur*<br/>
Ein `CComCurrency` -Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt `CComCurrency` ein Objekt zurück, das das Ergebnis der Subtraktion darstellt. Im Falle eines Fehlers, z. B. `AtlThrow` eines Überlaufs, ruft dieser Operator mit einem HRESULT auf, das den Fehler beschreibt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_neq"></a>CComCurrency::operator !=

Dieser Operator vergleicht zwei Objekte auf Ungleichheit.

```
bool operator!= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parameter

*Cur*<br/>
Das zu vergleichende `CComCurrency`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das verglichene Element nicht gleich dem `CComCurrency` Objekt ist. andernfalls FALSE.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_star"></a>CComCurrency::Operator *

Dieser Operator wird verwendet, um Multiplikation für ein `CComCurrency`-Objekt auszuführen.

```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parameter

*nOperand*<br/>
Der Multiplikator.

*Cur*<br/>
Das `CComCurrency` Objekt, das als Multiplikator verwendet wird.

### <a name="return-value"></a>Rückgabewert

Gibt `CComCurrency` ein Objekt zurück, das das Ergebnis der Multiplikation darstellt. Im Falle eines Fehlers, z. B. `AtlThrow` eines Überlaufs, ruft dieser Operator mit einem HRESULT auf, das den Fehler beschreibt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_star_eq"></a>CComCurrency::Operator\*=

Dieser Operator wird verwendet, um Multiplikation für ein `CComCurrency`-Objekt auszuführen und ihm das Ergebnis zuzuweisen.

```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parameter

*nOperand*<br/>
Der Multiplikator.

*Cur*<br/>
Das `CComCurrency` Objekt, das als Multiplikator verwendet wird.

### <a name="return-value"></a>Rückgabewert

Gibt das `CComCurrency` aktualisierte Objekt zurück. Im Falle eines Fehlers, z. B. `AtlThrow` eines Überlaufs, ruft dieser Operator mit einem HRESULT auf, das den Fehler beschreibt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_div"></a>CComCurrency::operator /

Dieser Operator wird verwendet, um Division für ein `CComCurrency`-Objekt auszuführen.

```
CComCurrency operator/(long nOperand) const;
```

### <a name="parameters"></a>Parameter

*nOperand*<br/>
Der Divisor.

### <a name="return-value"></a>Rückgabewert

Gibt `CComCurrency` ein Objekt zurück, das das Ergebnis der Division darstellt. Wenn der Divisor 0 ist, tritt ein Assertionsfehler auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_div_eq"></a>CComCurrency::operator /=

Dieser Operator wird verwendet, um Division für ein `CComCurrency`-Objekt auszuführen und ihm das Ergebnis zuzuweisen.

```
const CComCurrency& operator/= (long nOperand);
```

### <a name="parameters"></a>Parameter

*nOperand*<br/>
Der Divisor.

### <a name="return-value"></a>Rückgabewert

Gibt das `CComCurrency` aktualisierte Objekt zurück. Wenn der Divisor 0 ist, tritt ein Assertionsfehler auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_add"></a>CComCurrency::Operator +

Dieser Operator wird verwendet, um Addition für ein `CComCurrency`-Objekt auszuführen.

```
CComCurrency operator+(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parameter

*Cur*<br/>
Das `CComCurrency` Objekt, das dem ursprünglichen Objekt hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt `CComCurrency` ein Objekt zurück, das das Ergebnis des Hinzufügens darstellt. Im Falle eines Fehlers, z. B. `AtlThrow` eines Überlaufs, ruft dieser Operator mit einem HRESULT auf, das den Fehler beschreibt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_add_eq"></a>CComCurrency::Operator +=

Dieser Operator wird verwendet, um Addition für ein `CComCurrency`-Objekt auszuführen und das Ergebnis dem aktuellen Objekt zuzuweisen.

```
const CComCurrency& operator+= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parameter

*Cur*<br/>
Das `CComCurrency`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt das `CComCurrency` aktualisierte Objekt zurück. Im Falle eines Fehlers, z. B. `AtlThrow` eines Überlaufs, ruft dieser Operator mit einem HRESULT auf, das den Fehler beschreibt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]

## <a name="ccomcurrencyoperator-lt"></a><a name="operator_lt"></a>CComCurrency::Operator&lt;

Dieser Operator vergleicht zwei `CComCurrency`-Objekte, um das kleinere zu bestimmen.

```
bool operator<(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parameter

*Cur*<br/>
Ein `CComCurrency` -Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das erste Objekt kleiner als das zweite ist, ANDERNFALLS FALSE.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]

## <a name="ccomcurrencyoperator-lt"></a><a name="operator_lt_eq"></a>CComCurrency::Operator&lt;=

Dieser Operator vergleicht zwei `CComCurrency`-Objekte, um zu bestimmen, ob sie gleich sind oder welches kleiner ist.

```
bool operator<= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parameter

*Cur*<br/>
Ein `CComCurrency` -Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das erste Objekt kleiner oder gleich dem zweiten, andernfalls FALSE ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_eq"></a>CComCurrency::operator =

Dieser Operator weist dem `CComCurrency`-Objekt einen neuen Wert zu.

```
const CComCurrency& operator= (const CComCurrency& curSrc) throw();
const CComCurrency& operator= (CURRENCY cySrc) throw();
const CComCurrency& operator= (FLOAT fSrc);
const CComCurrency& operator= (SHORT sSrc);
const CComCurrency& operator= (LONG lSrc);
const CComCurrency& operator= (BYTE bSrc);
const CComCurrency& operator= (USHORT usSrc);
const CComCurrency& operator= (DOUBLE dSrc);
const CComCurrency& operator= (CHAR cSrc);
const CComCurrency& operator= (ULONG ulSrc);
const CComCurrency& operator= (DECIMAL dSrc);
```

### <a name="parameters"></a>Parameter

*curSrc*<br/>
Ein `CComCurrency` -Objekt.

*cySrc*<br/>
Eine Variable vom Typ CURRENCY.

*sSrc*, *fSrc*, *lSrc*, *bSrc*, *usSrc*, *dSrc*, *cSrc*, *ulSrc*, *dSrc*<br/>
Der numerische Wert, `CComCurrency` der dem Objekt zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt das `CComCurrency` aktualisierte Objekt zurück. Im Falle eines Fehlers, z. B. `AtlThrow` eines Überlaufs, ruft dieser Operator mit einem HRESULT auf, das den Fehler beschreibt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]

## <a name="ccomcurrencyoperator--"></a><a name="operator_-_eq"></a>CComCurrency::operator -=

Dieser Operator wird verwendet, um Subtraktion für ein `CComCurrency`-Objekt auszuführen und ihm das Ergebnis zuzuweisen.

```
const CComCurrency& operator-= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parameter

*Cur*<br/>
Ein `CComCurrency` -Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt das `CComCurrency` aktualisierte Objekt zurück. Im Falle eines Fehlers, z. B. `AtlThrow` eines Überlaufs, ruft dieser Operator mit einem HRESULT auf, das den Fehler beschreibt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_eq_eq"></a>CComCurrency::operator ==

Dieser Operator überprüft zwei `CComCurrency`-Objekte auf Gleichheit.

```
bool operator== (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parameter

*Cur*<br/>
Das zu vergleichende `CComCurrency`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Objekte `m_currency` gleich sind (d. h. die Datenmember, sowohl ganzzahlig als auch fraktioniert, in beiden Objekten den gleichen Wert haben), ANDERNFALLS FALSE.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]

## <a name="ccomcurrencyoperator-gt"></a><a name="operator_gt"></a>CComCurrency::Operator&gt;

Dieser Operator vergleicht zwei `CComCurrency`-Objekte, um das größere zu bestimmen.

```
bool operator>(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parameter

*Cur*<br/>
Ein `CComCurrency` -Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das erste Objekt größer als das zweite ist, ANDERNFALLS FALSE.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]

## <a name="ccomcurrencyoperator-gt"></a><a name="operator_gt_eq"></a>CComCurrency::Operator&gt;=

Dieser Operator vergleicht zwei `CComCurrency`-Objekte, um zu bestimmen, ob sie gleich sind oder welches größer ist.

```
bool operator>= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parameter

*Cur*<br/>
Ein `CComCurrency` -Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das erste Objekt größer oder gleich dem zweiten, andernfalls FALSE ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]

## <a name="ccomcurrencyoperator-currency"></a><a name="operator_currency"></a>CComCurrency::operator CURRENCY

Diese Operatoren werden `CComCurrency` verwendet, um ein Objekt in einen CURRENCY-Datentyp zu umwerfen.

```
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf ein CURRENCY-Objekt zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]

## <a name="ccomcurrencyround"></a><a name="round"></a>CComCurrency::Runde

Rufen Sie diese Methode auf, um die Währung auf eine angegebene Anzahl von Dezimalstellen zu runden.

```
HRESULT Roundint nDecimals);
```

### <a name="parameters"></a>Parameter

*nDezimal*<br/>
Die Anzahl der Ziffern, auf die `m_currency` gerundet wird, im Bereich von 0 bis 4.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]

## <a name="ccomcurrencysetfraction"></a><a name="setfraction"></a>CComCurrency::SetFraction

Rufen Sie diese Methode auf, um den Nachkommawert eines `CComCurrency`-Objekts festzulegen.

```
HRESULT SetFraction(SHORT nFraction);
```

### <a name="parameters"></a>Parameter

*nFraktion*<br/>
Der Wert, der der Bruchkomponente `m_currency` des Datenelements zugewiesen werden soll. Das Vorzeichen der Bruchkomponente muss mit der ganzzahligen Komponente identisch sein, und der Wert muss im Bereich -9999 (CY_MIN_FRACTION) bis +9999 (CY_MAX_FRACTION) liegen.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]

## <a name="ccomcurrencysetinteger"></a><a name="setinteger"></a>CComCurrency::SetInteger

Rufen Sie diese Methode auf, um den ganzzahligen Wert eines `CComCurrency`-Objekts festzulegen.

```
HRESULT SetInteger(LONGLONG nInteger);
```

### <a name="parameters"></a>Parameter

*nInteger*<br/>
Der Wert, der der ganzzahligen `m_currency` Komponente des Datenelements zugewiesen werden soll. Das Vorzeichen der ganzzahligen Komponente muss mit dem Vorzeichen der vorhandenen Bruchkomponente übereinstimmen.

*nInteger* muss im Bereich CY_MIN_INTEGER bis einschließlich CY_MAX_INTEGER liegen. Diese Werte werden in atlcur.h definiert.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]

## <a name="see-also"></a>Siehe auch

[COleCurrency-Klasse](../../mfc/reference/colecurrency-class.md)<br/>
[Währung](/windows/win32/api/wtypes/ns-wtypes-cy~r1)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
