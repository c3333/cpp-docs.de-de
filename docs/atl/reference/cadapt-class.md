---
title: CAdapt-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAdapt
- ATLCOMCLI/ATL::CAdapt
- ATLCOMCLI/ATL::CAdapt::CAdapt
- ATLCOMCLI/ATL::CAdapt::m_T
helpviewer_keywords:
- address-of operator
- adapter objects
- '& operator, address-of operator'
- CAdapt class
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
ms.openlocfilehash: 23544bc103de0d7b76cd73d403626ba93af6e31a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321640"
---
# <a name="cadapt-class"></a>CAdapt-Klasse

Diese Vorlage dient dazu, Klassen zu umschließen, die den Adressoperator so umdefinieren, dass eine andere als die Adresse des Objekts zurückgegeben wird.

## <a name="syntax"></a>Syntax

```
template <class T>
class CAdapt
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der angepasste Typ.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAdapt::CAdapt](#cadapt)|Der Konstruktor.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAdapt::operator const T&](#operator_const_t_amp)|Gibt einen **const-Verweis** auf `m_T`zurück.|
|[CAdapt::operator T&](#operator_t_amp)|Gibt einen Verweis auf `m_T`zurück.|
|[CAdapt::operator <](#operator_lt)|Vergleicht ein Objekt des angepassten Typs mit `m_T`.|
|[CAdapt::operator =](#operator_eq)|Weist `m_T` ein Objekt des angepassten Typs zu.|
|[CAdapt::operator ==](#operator_eq_eq)|Vergleicht ein Objekt des angepassten Typs mit `m_T`.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAdapt::m_T](#m_t)|Die Daten, die angepasst werden.|

## <a name="remarks"></a>Bemerkungen

`CAdapt` ist eine einfache Vorlage. Sie dient dazu, Klassen zu umschließen, die den Adressoperator (`operator &`) so umdefinieren, dass eine andere als die Adresse des Objekts zurückgegeben wird. Zu diesen Klassen gehören die ATL-Klassen `CComBSTR`, `CComPtr` und `CComQIPtr` sowie die Compilerklasse für die COM-Unterstützung `_com_ptr_t`. Diese Klassen definieren alle die Adresse des Operators neu, um die Adresse eines ihrer `CComBSTR`Datenmember zurückzugeben (ein BSTR im Fall von , und ein Schnittstellenzeiger im Fall der anderen Klassen).

`CAdapt`Die Hauptaufgabe von besteht darin, die durch klasse *T*definierte Adress-des Operators zu verbergen, aber dennoch die Eigenschaften der angepassten Klasse beizubehalten. `CAdapt`erfüllt diese Rolle, indem ein öffentliches Mitglied, [m_T](#m_t), vom Typ *T*, und durch die Definition `CAdapt` von Konvertierungsoperatoren, Vergleichsoperatoren und einem Kopierkonstruktor, um Spezialisierungen zu behandeln, als wären sie Objekte vom Typ *T*.

Die Adapterklasse `CAdapt` ist nützlich, da einige Containerklassen erwarten, dass sie Adressen der in ihnen enthaltenen Objekte unter Verwendung des Adressoperators abrufen können. Die Neudefinition des Adressoperators kann diese Anforderung vereiteln. Das führt in der Regel zu Kompilierungsfehlern und verhindert, dass der nicht angepasste Typ im Zusammenhang mit Klassen verwendet werden kann, die lediglich erwarten, dass er funktioniert. `CAdapt` stellt eine Methode zur Umgehung solcher Probleme bereit.

Normalerweise verwenden Sie `CAdapt`, wenn `CComBSTR`-, `CComPtr`-, `CComQIPtr`- oder `_com_ptr_t`-Objekte in einer Containerklasse gespeichert werden sollen. Das war bei C++-Standardbibliothekscontainern vor der Unterstützung des C++11-Standards der Regelfall. C++11- Standardbibliothekscontainer funktionieren allerdings automatisch mit Objekttypen, die überladene `operator&()`-Operatoren aufweisen. Die Standardbibliothek erreicht dies, indem sie [intern std::addressof](../../standard-library/memory-functions.md#addressof) verwendet, um die wahren Adressen von Objekten abzubekommen.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcomcli.h

## <a name="cadaptcadapt"></a><a name="cadapt"></a>CAdapt::CAdapt

Die Konstruktoren ermöglichen es, ein Adapterobjekt standardmäßig zu erstellen, aus einem Objekt des angepassten Typs oder aus einem anderen Adapterobjekt zu kopieren.

```
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parameter

*rSrc*<br/>
Eine Variable des Typs, der angepasst wird, um in das neu erstellte Adapterobjekt kopiert zu werden.

*rSrCA*<br/>
Ein Adapterobjekt, dessen enthaltene Daten in das neu erstellte Adapterobjekt kopiert (oder verschoben) werden sollen.

## <a name="cadaptm_t"></a><a name="m_t"></a>CAdapt::m_T

Hält die angepassten Daten.

```
T m_T;
```

### <a name="remarks"></a>Bemerkungen

Auf dieses **öffentliche** Datenmitglied kann direkt oder indirekt mit [dem Betreiber const T&](#operator_const_t_amp) und dem Betreiber T [&](#operator_t_amp)zugegriffen werden.

## <a name="cadaptoperator-const-tamp"></a><a name="operator_const_t_amp"></a>CAdapt::operator const T&amp;

Gibt einen **const-Verweis** auf das [m_T-Member](#m_t) zurück, sodass das Adapterobjekt so behandelt werden kann, als wäre es ein Objekt vom Typ *T*.

```
operator const T&() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **const-Verweis** auf `m_T`.

## <a name="cadaptoperator-tamp"></a><a name="operator_t_amp"></a>CAdapt::operator T&amp;

Gibt einen Verweis auf das [m_T-Member](#m_t) zurück, sodass das Adapterobjekt so behandelt werden kann, als wäre es ein Objekt vom Typ *T*.

```
operator T&();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf `m_T`.

## <a name="cadaptoperator-lt"></a><a name="operator_lt"></a>CAdapt::operator&lt;

Vergleicht ein Objekt des angepassten Typs mit [m_T](#m_t).

```
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>Parameter

*rSrc*<br/>
Ein Verweis auf das zu vergleichende Objekt.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des `m_T` Vergleichs zwischen und *rSrc*.

## <a name="cadaptoperator-"></a><a name="operator_eq"></a>CAdapt::operator =

Der Zuweisungsoperator weist das Argument *rSrc*dem Datenmember [m_T](#m_t) zu und gibt das aktuelle Adapterobjekt zurück.

```
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parameter

*rSrc*<br/>
Ein Verweis auf ein Objekt des angepassten Typs, das kopiert werden soll.

*rSrCA*<br/>
Ein Verweis auf ein zu verschiebendes Objekt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das aktuelle Objekt.

## <a name="cadaptoperator-"></a><a name="operator_eq_eq"></a>CAdapt::operator ==

Vergleicht ein Objekt des angepassten Typs mit [m_T](#m_t).

```
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>Parameter

*rSrc*<br/>
Ein Verweis auf das zu vergleichende Objekt.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des Vergleichs zwischen *m_T* und *rSrc*.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
