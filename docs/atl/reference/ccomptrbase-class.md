---
title: CComPtrBase-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase::Advise
- ATLCOMCLI/ATL::CComPtrBase::Attach
- ATLCOMCLI/ATL::CComPtrBase::CoCreateInstance
- ATLCOMCLI/ATL::CComPtrBase::CopyTo
- ATLCOMCLI/ATL::CComPtrBase::Detach
- ATLCOMCLI/ATL::CComPtrBase::IsEqualObject
- ATLCOMCLI/ATL::CComPtrBase::QueryInterface
- ATLCOMCLI/ATL::CComPtrBase::Release
- ATLCOMCLI/ATL::CComPtrBase::SetSite
- ATLCOMCLI/ATL::CComPtrBase::p
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
ms.openlocfilehash: 9c62cc912b3fea3ea68390882bdda37cbfb25a7e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747762"
---
# <a name="ccomptrbase-class"></a>CComPtrBase-Klasse

Diese Klasse bietet die Grundlage für intelligente Zeigerklassen, die COM-basierte Speicherroutinen verwenden.

## <a name="syntax"></a>Syntax

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Objekttyp, auf den der smarte Zeiger verweisen soll.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComPtrBase::'CComPtrBase](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComPtrBase::Beratung](#advise)|Rufen Sie diese Methode auf, um eine Verbindung zwischen dem `CComPtrBase`Verbindungspunkt von 's und der Senke eines Clients zu erstellen.|
|[CComPtrBase::Anfügen](#attach)|Rufen Sie diese Methode auf, um die Besitzverhältnisse eines vorhandenen Zeigers zu übernehmen.|
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|Rufen Sie diese Methode auf, um ein Objekt der Klasse zu erstellen, die einer angegebenen Klassen- oder Programm-ID zugeordnet ist.|
|[CComPtrBase::CopyTo](#copyto)|Rufen Sie diese `CComPtrBase` Methode auf, um den Zeiger in eine andere Zeigervariable zu kopieren.|
|[CComPtrBase::Detach](#detach)|Rufen Sie diese Methode auf, um den Besitz eines Zeigers freizugeben.|
|[CComPtrBase::IsEqualObject](#isequalobject)|Rufen Sie diese Methode `IUnknown` auf, um zu überprüfen, ob das angegebene Objekt auf dasselbe Objekt verweist, das dem `CComPtrBase` Objekt zugeordnet ist.|
|[CComPtrBase::QueryInterface](#queryinterface)|Rufen Sie diese Methode auf, um einen Zeiger auf eine angegebene Schnittstelle zurückzugeben.|
|[CComPtrBase::Release](#release)|Rufen Sie diese Methode auf, um die Schnittstelle freizugeben.|
|[CComPtrBase::SetSite](#setsite)|Rufen Sie diese Methode auf, um die Site des `CComPtrBase` Objekts auf das `IUnknown` übergeordnete Objekt festzulegen.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComPtrBase::operator T*](#operator_t_star)|Der Gussoperator.|
|[CComPtrBase::Operator !](#operator_not)|Der NOT-Operator.|
|[CComPtrBase::Operator &](#operator_amp)|Der Operator &.|
|[CComPtrBase::Operator *](#operator_star)|Der Operator \*.|
|[CComPtrBase::Operator <](#ccomptrbase__operator lt)|Der weniger als der Operator.|
|[CComPtrBase::operator ==](#operator_eq_eq)|Der Gleichheitsoperator.|
|[CComPtrBase::operator ->](#operator_ptr)|Der Zeiger-zu-Mitglieder-Operator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComPtrBase::p](#p)|Die Zeigerdatenmembervariable.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse bildet die Grundlage für andere intelligente Zeiger, die COM-Speicherverwaltungsroutinen verwenden, z. [B. CComQIPtr](../../atl/reference/ccomqiptr-class.md) und [CComPtr](../../atl/reference/ccomptr-class.md). Die abgeleiteten Klassen fügen eigene Konstruktoren und Operatoren `CComPtrBase`hinzu, verlassen sich jedoch auf die von bereitgestellten Methoden.

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlcomcli.h

## <a name="ccomptrbaseadvise"></a><a name="advise"></a>CComPtrBase::Beratung

Rufen Sie diese Methode auf, um eine Verbindung zwischen dem `CComPtrBase`Verbindungspunkt von 's und der Senke eines Clients zu erstellen.

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>Parameter

*Punk*<br/>
Ein Zeiger auf die `IUnknown`des Clients .

*Iid*<br/>
Die GUID des Verbindungspunkts. In der Regel entspricht dies der ausgehenden Schnittstelle, die vom Verbindungspunkt verwaltet wird.

*Pdw*<br/>
Ein Zeiger auf das Cookie, das die Verbindung eindeutig identifiziert.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [AtlAdvise.](connection-point-global-functions.md#atladvise)

## <a name="ccomptrbaseattach"></a><a name="attach"></a>CComPtrBase::Anfügen

Rufen Sie diese Methode auf, um die Besitzverhältnisse eines vorhandenen Zeigers zu übernehmen.

```cpp
void Attach(T* p2) throw();
```

### <a name="parameters"></a>Parameter

*p2*<br/>
Das `CComPtrBase` Objekt übernimmt den Besitz dieses Zeigers.

### <a name="remarks"></a>Bemerkungen

`Attach`ruft [CComPtrBase::Release](#release) für die vorhandene [CComPtrBase::p-Membervariable](#p) `CComPtrBase::p`auf und weist dann *p2* zu . Wenn `CComPtrBase` ein Objekt den Besitz eines Zeigers `Release` übernimmt, ruft es automatisch den Zeiger auf, der den Zeiger und alle zugeordneten Daten löscht, wenn die Verweisanzahl für das Objekt auf 0 geht.

## <a name="ccomptrbaseccomptrbase"></a><a name="dtor"></a>CComPtrBase::'CComPtrBase

Der Destruktor.

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt die Schnittstelle `CComPtrBase`frei, auf die von verwiesen wird.

## <a name="ccomptrbasecocreateinstance"></a><a name="cocreateinstance"></a>CComPtrBase::CoCreateInstance

Rufen Sie diese Methode auf, um ein Objekt der Klasse zu erstellen, die einer angegebenen Klassen- oder Programm-ID zugeordnet ist.

```
HRESULT CoCreateInstance(
    LPCOLESTR szProgID,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();

HRESULT CoCreateInstance(
    REFCLSID rclsid,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();
```

### <a name="parameters"></a>Parameter

*szProgID*<br/>
Zeiger auf eine ProgID, die zum Wiederherstellen der CLSID verwendet wird.

*pUnkOuter*<br/>
Wenn NULL, gibt an, dass das Objekt nicht als Teil eines Aggregats erstellt wird. Wenn nicht- NULL, ist ein Zeiger auf `IUnknown` die Schnittstelle `IUnknown`des Aggregatobjekts (das Steuern ).

*dwClsContext*<br/>
Kontext, in dem der Code ausgeführt wird, der das neu erstellte Objekt verwaltet.

*rclsid*<br/>
CLSID zugeordnet mit den Daten und dem Code, der zum Erstellen des Objekts verwendet wird.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK auf Erfolg oder REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING oder E_NOINTERFACE bei Einem Fehler zurück. Eine Beschreibung dieser Fehler finden Sie unter [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) und [CLSIDFromProgID.](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid)

### <a name="remarks"></a>Bemerkungen

Wenn die erste Form der Methode aufgerufen wird, wird [CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) verwendet, um die CLSID wiederherzustellen. Beide Formulare rufen dann [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)auf.

In Debugbuilds tritt ein Assertionsfehler auf, wenn [CComPtrBase::p](#p) nicht gleich NULL ist.

## <a name="ccomptrbasecopyto"></a><a name="copyto"></a>CComPtrBase::CopyTo

Rufen Sie diese `CComPtrBase` Methode auf, um den Zeiger in eine andere Zeigervariable zu kopieren.

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>Parameter

*Ppt*<br/>
Adresse der Variablen, die `CComPtrBase` den Zeiger empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK auf Erfolg zurück, E_POINTER auf Misserfolg.

### <a name="remarks"></a>Bemerkungen

Kopiert `CComPtrBase` den Zeiger auf *ppT*. Die Referenzanzahl für die [Membervariable CComPtrBase::p](#p) wird erhöht.

Ein Fehler HRESULT wird zurückgegeben, wenn *ppT* gleich NULL ist. In Debugbuilds tritt ein Assertionsfehler auf, wenn *ppT* gleich NULL ist.

## <a name="ccomptrbasedetach"></a><a name="detach"></a>CComPtrBase::Detach

Rufen Sie diese Methode auf, um den Besitz eines Zeigers freizugeben.

```
T* Detach() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt eine Kopie des Zeigers zurück.

### <a name="remarks"></a>Bemerkungen

Gibt den Besitz eines Zeigers frei, legt die Datenmembervariable [CComPtrBase::p](#p) auf NULL fest und gibt eine Kopie des Zeigers zurück.

## <a name="ccomptrbaseisequalobject"></a><a name="isequalobject"></a>CComPtrBase::IsEqualObject

Rufen Sie diese Methode `IUnknown` auf, um zu überprüfen, ob das angegebene Objekt auf dasselbe Objekt verweist, das dem `CComPtrBase` Objekt zugeordnet ist.

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>Parameter

*pOther*<br/>
Das zu vergleichende `IUnknown *`-Element.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Objekte identisch sind, andernfalls false.

## <a name="ccomptrbaseoperator-"></a><a name="operator_not"></a>CComPtrBase::Operator !

Der NOT-Operator.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true `CComHeapPtr` zurück, wenn der Zeiger gleich NULL ist, andernfalls false.

## <a name="ccomptrbaseoperator-amp"></a><a name="operator_amp"></a>CComPtrBase::Operator&amp;

Der Operator &.

```
T** operator&() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Adresse des Objekts `CComPtrBase` zurück, auf das das Objekt zeigt.

## <a name="ccomptrbaseoperator-"></a><a name="operator_star"></a>CComPtrBase::Operator\*

Der Operator \*.

```
T& operator*() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Wert von [CComPtrBase::p](#p)zurück. d. h. ein Zeiger auf das `CComPtrBase` Objekt, auf das das Objekt verweist.

Wenn das Debug-Builds erstellt wird, tritt ein Assertionsfehler auf, wenn [CComPtrBase::p](#p) nicht gleich NULL ist.

## <a name="ccomptrbaseoperator-"></a><a name="operator_eq_eq"></a>CComPtrBase::operator ==

Der Gleichheitsoperator.

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>Parameter

*Pt*<br/>
Ein Zeiger auf ein Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt true `CComPtrBase` if und *pT-Punkt* auf dasselbe Objekt zurück, andernfalls false.

## <a name="ccomptrbaseoperator--gt"></a><a name="operator_ptr"></a>CComPtrBase::Operator -&gt;

Der Zeiger-zu-Member-Operator.

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Wert der Datenmembervariablen [CComPtrBase::p](#p) zurück.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Operator, um eine Methode `CComPtrBase` in einer Klasse aufzurufen, auf die das Objekt zeigt. In Debugbuilds tritt ein Assertionsfehler auf, wenn der `CComPtrBase` Datenmember auf NULL verweist.

## <a name="ccomptrbaseoperator-lt"></a><a name="operator_lt"></a>CComPtrBase::Operator&lt;

Der weniger als der Operator.

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>Parameter

*Pt*<br/>
Ein Zeiger auf ein Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Zeiger, der vom aktuellen Objekt verwaltet wird, kleiner ist als der Zeiger, mit dem er verglichen wird.

## <a name="ccomptrbaseoperator-t"></a><a name="operator_t_star"></a>CComPtrBase::operator T\*

Der Gussoperator.

```
operator T*() const throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt einen Zeiger auf den in der Klassenvorlage definierten Objektdatentyp zurück.

## <a name="ccomptrbasep"></a><a name="p"></a>CComPtrBase::p

Die Zeigerdatenmembervariable.

```
T* p;
```

### <a name="remarks"></a>Bemerkungen

Diese Membervariable enthält die Zeigerinformationen.

## <a name="ccomptrbasequeryinterface"></a><a name="queryinterface"></a>CComPtrBase::QueryInterface

Rufen Sie diese Methode auf, um einen Zeiger auf eine angegebene Schnittstelle zurückzugeben.

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>Parameter

*Q*<br/>
Der Objekttyp, dessen Schnittstellenzeiger erforderlich ist.

*Pp*<br/>
Adresse der Ausgabevariablen, die den angeforderten Schnittstellenzeiger empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK auf Erfolg oder E_NOINTERFACE bei Einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))auf.

In Debugbuilds tritt ein Assertionsfehler auf, wenn *pp* nicht gleich NULL ist.

## <a name="ccomptrbaserelease"></a><a name="release"></a>CComPtrBase::Release

Rufen Sie diese Methode auf, um die Schnittstelle freizugeben.

```cpp
void Release() throw();
```

### <a name="remarks"></a>Bemerkungen

Die Schnittstelle wird freigegeben, und [CComPtrBase::p](#p) ist auf NULL festgelegt.

## <a name="ccomptrbasesetsite"></a><a name="setsite"></a>CComPtrBase::SetSite

Rufen Sie diese Methode auf, um die Site des `CComPtrBase` Objekts auf das `IUnknown` übergeordnete Objekt festzulegen.

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>Parameter

*punkParent*<br/>
Ein Zeiger auf `IUnknown` die Schnittstelle des übergeordneten Elements.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite)auf.

## <a name="see-also"></a>Weitere Informationen

[Klassenübersicht](../../atl/atl-class-overview.md)
