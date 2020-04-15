---
title: CAutoPtr-Klasse
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
ms.openlocfilehash: cb8e3d6b71db6ab60b3b246bd8c5bf4f2c9aaa34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321257"
---
# <a name="cautoptr-class"></a>CAutoPtr-Klasse

Diese Klasse stellt ein intelligentes Zeigerobjekt dar.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <typename T>
class CAutoPtr
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Zeigertyp.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAutoPtr::CAutoPtr](#cautoptr)|Der Konstruktor.|
|[CAutoPtr::'CAutoPtr](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAutoPtr::Anfügen](#attach)|Rufen Sie diese Methode auf, um die Besitzverhältnisse eines vorhandenen Zeigers zu übernehmen.|
|[CAutoPtr::Detach](#detach)|Rufen Sie diese Methode auf, um den Besitz eines Zeigers freizugeben.|
|[CAutoPtr::Kostenlos](#free)|Rufen Sie diese Methode auf, `CAutoPtr`um ein Objekt zu löschen, auf das von einem verwiesen wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAutoPtr::operator T*](#operator_t_star)|Der Gussoperator.|
|[CAutoPtr::operator =](#operator_eq)|Der Zuweisungsoperator.|
|[CAutoPtr::operator ->](#operator_ptr)|Der Zeiger-zu-Member-Operator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAutoPtr::m_p](#m_p)|Die Zeigerdatenmembervariable.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt Methoden zum Erstellen und Verwalten eines intelligenten Zeigers bereit, der zum Schutz vor Speicherverlusten beiträgt, indem Ressourcen automatisch freiwerden, wenn er nicht in den Gültigkeitsbereich fällt.

`CAutoPtr`Darüber hinaus überträgt der Kopierkonstruktor und der Zuweisungsoperator den Besitz des Zeigers, kopiert den Quellzeiger in den Zielzeiger und setzt den Quellzeiger auf NULL. Es ist daher unmöglich, zwei `CAutoPtr` Objekte zu haben, die jeweils denselben Zeiger speichern, und dies verringert die Möglichkeit, denselben Zeiger zweimal zu löschen.

`CAutoPtr`vereinfacht auch die Erstellung von Sammlungen von Zeigern. Anstatt eine Auflistungsklasse abzuleiten und den Destruktor zu überschreiben, `CAutoPtr` ist es einfacher, eine Auflistung von Objekten zu erstellen. Wenn die Auflistung gelöscht `CAutoPtr` wird, werden die Objekte aus dem Gültigkeitsbereich entfernt und werden automatisch selbst gelöscht.

[CHeapPtr](../../atl/reference/cheapptr-class.md) und Varianten funktionieren auf `CAutoPtr`die gleiche Weise wie , mit der Ausnahme, dass sie Speicher mit verschiedenen Heapfunktionen anstelle der C++ **new-** und **delete-Operatoren** zuweisen und frei machen. [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) ist `CAutoPtr`ähnlich wie , der einzige Unterschied ist, dass es **Vektor new[]** und **Vektor delete[]** verwendet, um Speicher zuzuweisen und freizugeben.

Siehe auch [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) und [CAutoPtrList,](../../atl/reference/cautoptrlist-class.md) wenn Arrays oder Listen von intelligenten Zeigern erforderlich sind.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

## <a name="cautoptrattach"></a><a name="attach"></a>CAutoPtr::Anfügen

Rufen Sie diese Methode auf, um die Besitzverhältnisse eines vorhandenen Zeigers zu übernehmen.

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Das `CAutoPtr` Objekt übernimmt den Besitz dieses Zeigers.

### <a name="remarks"></a>Bemerkungen

Wenn `CAutoPtr` ein Objekt den Besitz eines Zeigers übernimmt, löscht es automatisch den Zeiger und alle zugeordneten Daten, wenn es den Gültigkeitsbereich verlässt. Wenn [CAutoPtr::Detach](#detach) aufgerufen wird, wird dem Programmierer erneut die Verantwortung für die Freigabe der zugewiesenen Ressourcen übertragen.

In Debugbuilds tritt ein Assertionsfehler auf, wenn das [CAutoPtr::m_p](#m_p) Datenmember derzeit auf einen vorhandenen Wert verweist. das heißt, es ist nicht gleich NULL.

### <a name="example"></a>Beispiel

Siehe das Beispiel in der [CAutoPtr Übersicht](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="cautoptr"></a>CAutoPtr::CAutoPtr

Der Konstruktor.

```
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Ein vorhandener Zeiger.

*TSrc*<br/>
Der Typ, der `CAutoPtr`von einem anderen verwaltet wird, wird zum Initialisieren des aktuellen Objekts verwendet.

### <a name="remarks"></a>Bemerkungen

Das `CAutoPtr` Objekt kann mit einem vorhandenen Zeiger erstellt werden, in diesem Fall überträgt es den Besitz des Zeigers.

### <a name="example"></a>Beispiel

Siehe das Beispiel in der [CAutoPtr Übersicht](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="dtor"></a>CAutoPtr::'CAutoPtr

Der Destruktor.

```
~CAutoPtr() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugewiesenen Ressourcen frei. Ruft [CAutoPtr::Free](#free)auf.

## <a name="cautoptrdetach"></a><a name="detach"></a>CAutoPtr::Detach

Rufen Sie diese Methode auf, um den Besitz eines Zeigers freizugeben.

```
T* Detach() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt eine Kopie des Zeigers zurück.

### <a name="remarks"></a>Bemerkungen

Gibt den Besitz eines Zeigers frei, legt die Datenmembervariable [CAutoPtr::m_p](#m_p) auf NULL fest und gibt eine Kopie des Zeigers zurück. Nach `Detach`dem Aufruf ist es Aufgabe des Programmierers, `CAutoPtr` alle zugewiesenen Ressourcen freizugeben, über die das Objekt zuvor die Reponsibilität angenommen haben kann.

### <a name="example"></a>Beispiel

Siehe das Beispiel in der [CAutoPtr Übersicht](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrfree"></a><a name="free"></a>CAutoPtr::Kostenlos

Rufen Sie diese Methode auf, `CAutoPtr`um ein Objekt zu löschen, auf das von einem verwiesen wird.

```
void Free() throw();
```

### <a name="remarks"></a>Bemerkungen

Das Objekt, auf `CAutoPtr` das der zeigt, wird freigegeben, und die Datenmembervariable [CAutoPtr::m_p](#m_p) wird auf NULL gesetzt.

## <a name="cautoptrm_p"></a><a name="m_p"></a>CAutoPtr::m_p

Die Zeigerdatenmembervariable.

```
T* m_p;
```

### <a name="remarks"></a>Bemerkungen

Diese Membervariable enthält die Zeigerinformationen.

## <a name="cautoptroperator-"></a><a name="operator_eq"></a>CAutoPtr::operator =

Der Zuweisungsoperator.

```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>Parameter

*P*<br/>
Ein Zeiger.

*TSrc*<br/>
Ein Klassentyp.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf einen **CAutoPtr\< T >** zurück.

### <a name="remarks"></a>Bemerkungen

Der Zuweisungsoperator trennt `CAutoPtr` das Objekt von einem beliebigen aktuellen Zeiger und fügt den neuen Zeiger *p*an seiner Stelle an.

### <a name="example"></a>Beispiel

Siehe das Beispiel in der [CAutoPtr Übersicht](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator--gt"></a><a name="operator_ptr"></a>CAutoPtr::Operator -&gt;

Der Zeiger-zu-Member-Operator.

```
T* operator->() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Wert der Datenmembervariablen [CAutoPtr::m_p](#m_p) zurück.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Operator, um eine Methode `CAutoPtr` in einer Klasse aufzurufen, auf die das Objekt zeigt. In Debugbuilds tritt ein Assertionsfehler auf, wenn die `CAutoPtr` Punkte auf NULL gesetzt werden.

### <a name="example"></a>Beispiel

Siehe das Beispiel in der [CAutoPtr Übersicht](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator-t"></a><a name="operator_t_star"></a>CAutoPtr::operator T*

Der Gussoperator.

```
operator T* () const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den in der Klassenvorlage definierten Objektdatentyp zurück.

### <a name="example"></a>Beispiel

Siehe das Beispiel in der [CAutoPtr Übersicht](../../atl/reference/cautoptr-class.md).

## <a name="see-also"></a>Siehe auch

[CHeapPtr-Klasse](../../atl/reference/cheapptr-class.md)<br/>
[CAutoVectorPtr-Klasse](../../atl/reference/cautovectorptr-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
