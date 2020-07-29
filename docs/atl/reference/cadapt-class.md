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
ms.openlocfilehash: 2ea8fc8a26642abf593c7f4df3928ff90e66e2b3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229999"
---
# <a name="cadapt-class"></a>CAdapt-Klasse

Diese Vorlage dient dazu, Klassen zu umschließen, die den Adressoperator so umdefinieren, dass eine andere als die Adresse des Objekts zurückgegeben wird.

## <a name="syntax"></a>Syntax

```cpp
template <class T>
class CAdapt
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der angepasste Typ.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[CAdapt:: CAdapt](#cadapt)|Der Konstruktor.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAdapt:: Operator Konstanten T-&](#operator_const_t_amp)|Gibt einen **`const`** Verweis auf zurück `m_T` .|
|[CAdapt:: Operator T-&](#operator_t_amp)|Gibt einen Verweis auf `m_T`zurück.|
|[CAdapt:: Operator-<](#operator_lt)|Vergleicht ein Objekt des angepassten Typs mit `m_T`.|
|[CAdapt:: Operator =](#operator_eq)|Weist `m_T` ein Objekt des angepassten Typs zu.|
|[CAdapt:: Operator = =](#operator_eq_eq)|Vergleicht ein Objekt des angepassten Typs mit `m_T`.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAdapt:: m_T](#m_t)|Die Daten, die angepasst werden.|

## <a name="remarks"></a>Bemerkungen

`CAdapt` ist eine einfache Vorlage. Sie dient dazu, Klassen zu umschließen, die den Adressoperator (`operator &`) so umdefinieren, dass eine andere als die Adresse des Objekts zurückgegeben wird. Zu diesen Klassen gehören die ATL-Klassen `CComBSTR`, `CComPtr` und `CComQIPtr` sowie die Compilerklasse für die COM-Unterstützung `_com_ptr_t`. Diese Klassen definieren alle den Address-of-Operator, um die Adresse von einem Ihrer Datenmember (ein BSTR im Fall von `CComBSTR` ) und einen Schnittstellen Zeiger im Fall der anderen Klassen zurückzugeben.

`CAdapt`die primäre Rolle besteht darin, den Address-of-Operator auszublenden, der durch Klasse *T*definiert ist, aber dennoch die Merkmale der angepassten Klasse beizubehalten. `CAdapt`erfüllt diese Rolle, indem ein öffentliches Element, [m_T](#m_t), vom Typ *t*und durch Definieren von Konvertierungs Operatoren, Vergleichs Operatoren und einem Kopierkonstruktor festgelegt werden, damit Spezialisierungs Elemente `CAdapt` so behandelt werden, als wären Sie Objekte vom Typ *t*.

Die Adapterklasse `CAdapt` ist nützlich, da einige Containerklassen erwarten, dass sie Adressen der in ihnen enthaltenen Objekte unter Verwendung des Adressoperators abrufen können. Die Neudefinition des Adressoperators kann diese Anforderung vereiteln. Das führt in der Regel zu Kompilierungsfehlern und verhindert, dass der nicht angepasste Typ im Zusammenhang mit Klassen verwendet werden kann, die lediglich erwarten, dass er funktioniert. `CAdapt` stellt eine Methode zur Umgehung solcher Probleme bereit.

Normalerweise verwenden Sie `CAdapt`, wenn `CComBSTR`-, `CComPtr`-, `CComQIPtr`- oder `_com_ptr_t`-Objekte in einer Containerklasse gespeichert werden sollen. Das war bei C++-Standardbibliothekscontainern vor der Unterstützung des C++11-Standards der Regelfall. C++11- Standardbibliothekscontainer funktionieren allerdings automatisch mit Objekttypen, die überladene `operator&()`-Operatoren aufweisen. Die Standard Bibliothek erreicht dies durch die interne Verwendung von [Std:: AddressOf](../../standard-library/memory-functions.md#addressof) , um die tatsächlichen Adressen von Objekten zu erhalten.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlcomcli. h

## <a name="cadaptcadapt"></a><a name="cadapt"></a>CAdapt:: CAdapt

Mit den Konstruktoren kann ein Adapter Objekt standardmäßig erstellt, von einem Objekt des angepassten Typs kopiert oder von einem anderen Adapter Objekt kopiert werden.

```cpp
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parameter

*rSrc*<br/>
Eine Variable des Typs, der angepasst wird, um in das neu erstellte Adapter Objekt kopiert zu werden.

*rsrca*<br/>
Ein Adapter Objekt, dessen enthaltene Daten in das neu erstellte Adapter Objekt kopiert (oder verschoben) werden sollen.

## <a name="cadaptm_t"></a><a name="m_t"></a>CAdapt:: m_T

Enthält die Daten, die angepasst werden.

```cpp
T m_T;
```

### <a name="remarks"></a>Bemerkungen

Der **`public`** Zugriff auf diesen Datenmember ist direkt oder indirekt mit [Operator Konstanten t&](#operator_const_t_amp) und [Operator T&](#operator_t_amp)möglich.

## <a name="cadaptoperator-const-tamp"></a><a name="operator_const_t_amp"></a>CAdapt:: Operator Konstanten T&amp;

Gibt einen **`const`** Verweis auf den [m_T](#m_t) Member zurück, sodass das Adapter Objekt so behandelt werden kann, als wäre es ein Objekt vom Typ *T*.

```cpp
operator const T&() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **`const`** Verweis auf `m_T` .

## <a name="cadaptoperator-tamp"></a><a name="operator_t_amp"></a>CAdapt:: Operator T&amp;

Gibt einen Verweis auf den [m_T](#m_t) Member zurück, sodass das Adapter Objekt so behandelt werden kann, als wäre es ein Objekt vom Typ *T*.

```cpp
operator T&();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf `m_T`.

## <a name="cadaptoperator-lt"></a><a name="operator_lt"></a>CAdapt::-Operator&lt;

Vergleicht ein Objekt des angepassten Typs mit [m_T](#m_t).

```cpp
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>Parameter

*rSrc*<br/>
Ein Verweis auf das Objekt, das verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des Vergleichs zwischen `m_T` und *rsrc*.

## <a name="cadaptoperator-"></a><a name="operator_eq"></a>CAdapt:: Operator =

Der Zuweisungs Operator weist das Argument *rsrc*dem Datenmember [m_T](#m_t) und gibt das aktuelle Adapter Objekt zurück.

```cpp
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parameter

*rSrc*<br/>
Ein Verweis auf ein Objekt des angepassten Typs, der kopiert werden soll.

*rsrca*<br/>
Ein Verweis auf ein Objekt, das verschoben werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das aktuelle-Objekt.

## <a name="cadaptoperator-"></a><a name="operator_eq_eq"></a>CAdapt:: Operator = =

Vergleicht ein Objekt des angepassten Typs mit [m_T](#m_t).

```cpp
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>Parameter

*rSrc*<br/>
Ein Verweis auf das Objekt, das verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des Vergleichs zwischen *m_T* und *rsrc*.

## <a name="see-also"></a>Weitere Informationen

[Klassenübersicht](../../atl/atl-class-overview.md)
