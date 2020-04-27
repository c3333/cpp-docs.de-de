---
title: Cautoptr-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
helpviewer_keywords:
- CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
ms.openlocfilehash: 7f15e16b075b9a5327723a7f081100313f14ea77
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167720"
---
# <a name="cautoptr-class"></a>Cautoptr-Klasse

Diese Klasse stellt ein intelligentes Zeiger Objekt dar.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
template <typename T>
class CAutoPtr
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Zeigertyp.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cautoptr:: cautoptr](#cautoptr)|Der Konstruktor.|
|[Cautoptr:: ~ cautoptr](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cautoptr:: Attach](#attach)|Ruft diese Methode auf, um den Besitz eines vorhandenen Zeigers zu übernehmen.|
|[Cautoptr::D Etach](#detach)|Ruft diese Methode auf, um den Besitz eines Zeigers freizugeben.|
|[Cautoptr:: Free](#free)|Mit dieser Methode können Sie ein Objekt löschen, auf das `CAutoPtr`von verwiesen wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cautoptr:: Operator T *](#operator_t_star)|Der Umwandlungs Operator.|
|[Cautoptr:: Operator =](#operator_eq)|Der Zuweisungs Operator.|
|[Cautoptr:: Operator->](#operator_ptr)|Der Pointer-to-Member-Operator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cautoptr:: m_p](#m_p)|Die Zeiger Datenelement Variable.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt Methoden zum Erstellen und Verwalten eines intelligenten Zeigers bereit, der zum Schutz vor Speicher Verlusten beiträgt, indem Ressourcen automatisch freigegeben werden, wenn Sie den Gültigkeitsbereich verlassen.

`CAutoPtr`Darüber hinaus übertragen der Kopierkonstruktor und der Zuweisungs Operator den Besitz des Zeigers, kopieren den Quell Zeiger auf den Ziel Zeiger und legen den Quell Zeiger auf NULL fest. Es ist daher unmöglich, dass zwei `CAutoPtr` Objekte jeweils denselben Zeiger speichern. Dies verringert die Möglichkeit, denselben Zeiger zweimal zu löschen.

`CAutoPtr`vereinfacht auch das Erstellen von Auflistungen von Zeigern. Anstatt eine Auflistungs Klasse zu ableiten und den Dekonstruktor zu überschreiben, ist es einfacher `CAutoPtr` , eine Auflistung von-Objekten zu erstellen. Wenn die Auflistung gelöscht wird, werden `CAutoPtr` die Objekte außerhalb des Gültigkeits Bereichs und automatisch gelöscht.

Die Funktionen " [cheapptr](../../atl/reference/cheapptr-class.md) " und "Variant" `CAutoPtr`funktionieren auf die gleiche Weise wie, mit der Ausnahme, dass Sie Speicher mit unterschiedlichen Heap Funktionen anstelle der C++-Operatoren **New** und **Delete** zuordnen und freigeben. [Cautovector PTR](../../atl/reference/cautovectorptr-class.md) ähnelt `CAutoPtr`, der einzige Unterschied darin, dass " **Vector New []** " und " **Vector delete []** " zum Zuordnen und Freigeben von Arbeitsspeicher verwendet werden.

Siehe auch [cautoptrarray](../../atl/reference/cautoptrarray-class.md) und [cautoptrlist](../../atl/reference/cautoptrlist-class.md) , wenn Arrays oder Listen intelligenter Zeiger benötigt werden.

## <a name="requirements"></a>Anforderungen

**Header:** atlbase. h

## <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

## <a name="cautoptrattach"></a><a name="attach"></a>Cautoptr:: Attach

Ruft diese Methode auf, um den Besitz eines vorhandenen Zeigers zu übernehmen.

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parameter

*cker*<br/>
Das `CAutoPtr` Objekt übernimmt den Besitz dieses Zeigers.

### <a name="remarks"></a>Bemerkungen

Wenn ein `CAutoPtr` -Objekt in den Besitz eines Zeigers übergeht, werden der Zeiger und alle zugeordneten Daten automatisch gelöscht, wenn der Gültigkeitsbereich verlässt. Wenn [cautoptr::D Etach](#detach) aufgerufen wird, erhält der Programmierer erneut die Verantwortung für die Freigabe zugeordneter Ressourcen.

In Debugbuilds tritt ein Fehler auf, wenn das [cautoptr:: m_p](#m_p) -Datenmember aktuell auf einen vorhandenen Wert verweist. Das heißt, es ist nicht gleich NULL.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel in der [Übersicht über cautoptr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="cautoptr"></a>Cautoptr:: cautoptr

Der Konstruktor.

```cpp
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>Parameter

*cker*<br/>
Ein vorhandener-Zeiger.

*Wahrheits-RC*<br/>
Der von einem anderen `CAutoPtr`verwaltete Typ, der zum Initialisieren des aktuellen-Objekts verwendet wird.

### <a name="remarks"></a>Bemerkungen

Das `CAutoPtr` Objekt kann mit einem vorhandenen Zeiger erstellt werden. in diesem Fall überträgt es den Besitz des Zeigers.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel in der [Übersicht über cautoptr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="dtor"></a>Cautoptr:: ~ cautoptr

Der Destruktor.

```cpp
~CAutoPtr() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugeordneten Ressourcen frei. Ruft [cautoptr:: Free](#free)auf.

## <a name="cautoptrdetach"></a><a name="detach"></a>Cautoptr::D Etach

Ruft diese Methode auf, um den Besitz eines Zeigers freizugeben.

```cpp
T* Detach() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt eine Kopie des Zeigers zurück.

### <a name="remarks"></a>Bemerkungen

Gibt den Besitz eines Zeigers frei, legt die [cautoptr:: m_p](#m_p) -Datenmember-Variable auf NULL fest und gibt eine Kopie des Zeigers zurück. Nachdem aufgerufen `Detach`wurde, ist es dem Programmierer überlassen, alle zugeordneten Ressourcen freizugeben `CAutoPtr` , über die das Objekt möglicherweise zuvor die repktivität angenommen hat.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel in der [Übersicht über cautoptr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrfree"></a><a name="free"></a>Cautoptr:: Free

Mit dieser Methode können Sie ein Objekt löschen, auf das `CAutoPtr`von verwiesen wird.

```cpp
void Free() throw();
```

### <a name="remarks"></a>Bemerkungen

Das Objekt, auf das `CAutoPtr` verweist, wird freigegeben, und die [cautoptr:: m_p](#m_p) -Datenmember-Variable wird auf NULL festgelegt.

## <a name="cautoptrm_p"></a><a name="m_p"></a>Cautoptr:: m_p

Die Zeiger Datenelement Variable.

```cpp
T* m_p;
```

### <a name="remarks"></a>Bemerkungen

Diese Member-Variable enthält die Zeiger Informationen.

## <a name="cautoptroperator-"></a><a name="operator_eq"></a>Cautoptr:: Operator =

Der Zuweisungs Operator.

```cpp
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>Parameter

*cker*<br/>
Ein-Zeiger.

*Wahrheits-RC*<br/>
Ein Klassentyp.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf eine **cautoptr\< T-#b0 **zurück.

### <a name="remarks"></a>Bemerkungen

Der Zuweisungs Operator trennt das `CAutoPtr` Objekt von allen aktuellen Zeigern und fügt den neuen Zeiger *p*an seiner Stelle an.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel in der [Übersicht über cautoptr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator--gt"></a><a name="operator_ptr"></a>Cautoptr:: Operator-&gt;

Der Pointer-to-Member-Operator.

```cpp
T* operator->() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Wert der [cautoptr:: m_p](#m_p) -Datenmember-Variable zurück.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Operator, um eine Methode in einer Klasse aufzurufen, `CAutoPtr` auf die vom-Objekt verwiesen wird. In Debugbuilds tritt ein Assertionsfehler auf, `CAutoPtr` wenn auf NULL zeigt.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel in der [Übersicht über cautoptr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator-t"></a><a name="operator_t_star"></a>Cautoptr:: Operator T *

Der Umwandlungs Operator.

```cpp
operator T* () const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den in der Klassen Vorlage definierten Objekt Datentyp zurück.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel in der [Übersicht über cautoptr](../../atl/reference/cautoptr-class.md).

## <a name="see-also"></a>Weitere Informationen:

[Cheapptr-Klasse](../../atl/reference/cheapptr-class.md)<br/>
[Cautovectorptr-Klasse](../../atl/reference/cautovectorptr-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
