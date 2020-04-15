---
title: CAutoVectorPtr-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::Allocate
- ATLBASE/ATL::CAutoVectorPtr::Attach
- ATLBASE/ATL::CAutoVectorPtr::Detach
- ATLBASE/ATL::CAutoVectorPtr::Free
- ATLBASE/ATL::CAutoVectorPtr::m_p
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
ms.openlocfilehash: 573446256aa89423837ebf73176a73f72054911b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318768"
---
# <a name="cautovectorptr-class"></a>CAutoVectorPtr-Klasse

Diese Klasse stellt ein intelligentes Zeigerobjekt mit Vektor-Neu- und Löschoperatoren dar.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<typename T>
class CAutoVectorPtr
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Zeigertyp.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|Der Konstruktor.|
|[CAutoVectorPtr::'CAutoVectorPtr](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAutoVectorPtr::Zuweisen](#allocate)|Rufen Sie diese Methode auf, um den Speicher `CAutoVectorPtr`zuzuweisen, der für das Array von Objekten erforderlich ist, auf das von verwiesen wird.|
|[CAutoVectorPtr::Anfügen](#attach)|Rufen Sie diese Methode auf, um die Besitzverhältnisse eines vorhandenen Zeigers zu übernehmen.|
|[CAutoVectorPtr::Detach](#detach)|Rufen Sie diese Methode auf, um den Besitz eines Zeigers freizugeben.|
|[CAutoVectorPtr::Kostenlos](#free)|Rufen Sie diese Methode auf, `CAutoVectorPtr`um ein Objekt zu löschen, auf das von einem verwiesen wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAutoVectorPtr::Operator T *](#operator_t__star)|Der Gussoperator.|
|[CAutoVectorPtr::Operator =](#operator_eq)|Der Zuweisungsoperator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAutoVectorPtr::m_p](#m_p)|Die Zeigerdatenmembervariable.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt Methoden zum Erstellen und Verwalten eines intelligenten Zeigers bereit, der zum Schutz vor Speicherverlusten beiträgt, indem Ressourcen automatisch freiwerden, wenn er nicht in den Gültigkeitsbereich fällt. `CAutoVectorPtr`ist ähnlich `CAutoPtr`wie , der `CAutoVectorPtr` einzige Unterschied ist, dass [Vektor neue&#91;&#93;](../../standard-library/new-operators.md#op_new_arr) und Vektor löschen [&#91;&#93;](../../standard-library/new-operators.md#op_delete_arr) speicherzuteilen und freizugeben anstelle der C++ **new** und **delete** Operatoren. Siehe [CAutoVectorPtrElementTraits,](../../atl/reference/cautovectorptrelementtraits-class.md) wenn `CAutoVectorPtr` Auflistungsklassen von erforderlich sind.

Ein Beispiel für die Verwendung einer intelligenten Zeigerklasse finden Sie unter [CAutoPtr.](../../atl/reference/cautoptr-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="cautovectorptrallocate"></a><a name="allocate"></a>CAutoVectorPtr::Zuweisen

Rufen Sie diese Methode auf, um den Speicher `CAutoVectorPtr`zuzuweisen, der für das Array von Objekten erforderlich ist, auf das von verwiesen wird.

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>Parameter

*nElements*<br/>
Die Anzahl der Elemente im Array.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Speicher erfolgreich zugewiesen wurde, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn die [Membervariable CAutoVectorPtr::m_p](#m_p) derzeit auf einen vorhandenen Wert verweist. das heißt, es ist nicht gleich NULL.

## <a name="cautovectorptrattach"></a><a name="attach"></a>CAutoVectorPtr::Anfügen

Rufen Sie diese Methode auf, um die Besitzverhältnisse eines vorhandenen Zeigers zu übernehmen.

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Das `CAutoVectorPtr` Objekt übernimmt den Besitz dieses Zeigers.

### <a name="remarks"></a>Bemerkungen

Wenn `CAutoVectorPtr` ein Objekt den Besitz eines Zeigers übernimmt, löscht es automatisch den Zeiger und alle zugeordneten Daten, wenn es den Gültigkeitsbereich verlässt. Wenn [CAutoVectorPtr::Detach](#detach) aufgerufen wird, wird dem Programmierer erneut die Verantwortung für die Freigabe der zugewiesenen Ressourcen übertragen.

In Debugbuilds tritt ein Assertionsfehler auf, wenn die [Membervariable CAutoVectorPtr::m_p](#m_p) derzeit auf einen vorhandenen Wert verweist. das heißt, es ist nicht gleich NULL.

## <a name="cautovectorptrcautovectorptr"></a><a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr

Der Konstruktor.

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Ein vorhandener Zeiger.

### <a name="remarks"></a>Bemerkungen

Das `CAutoVectorPtr` Objekt kann mit einem vorhandenen Zeiger erstellt werden, in diesem Fall überträgt es den Besitz des Zeigers.

## <a name="cautovectorptrcautovectorptr"></a><a name="dtor"></a>CAutoVectorPtr::'CAutoVectorPtr

Der Destruktor.

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugewiesenen Ressourcen frei. Ruft [CAutoVectorPtr::Free](#free)auf.

## <a name="cautovectorptrdetach"></a><a name="detach"></a>CAutoVectorPtr::Detach

Rufen Sie diese Methode auf, um den Besitz eines Zeigers freizugeben.

```
T* Detach() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt eine Kopie des Zeigers zurück.

### <a name="remarks"></a>Bemerkungen

Gibt den Besitz eines Zeigers frei, legt die [Membervariable CAutoVectorPtr::m_p](#m_p) auf NULL fest und gibt eine Kopie des Zeigers zurück. Nach `Detach`dem Aufruf ist es Sache des Programmierers, `CAutoVectorPtr` alle zugewiesenen Ressourcen freizugeben, für die das Objekt zuvor möglicherweise die Verantwortung übernommen hat.

## <a name="cautovectorptrfree"></a><a name="free"></a>CAutoVectorPtr::Kostenlos

Rufen Sie diese Methode auf, `CAutoVectorPtr`um ein Objekt zu löschen, auf das von einem verwiesen wird.

```
void Free() throw();
```

### <a name="remarks"></a>Bemerkungen

Das Objekt, auf `CAutoVectorPtr` das der zeigt, wird freigegeben, und die Membervariable [CAutoVectorPtr::m_p](#m_p) wird auf NULL gesetzt.

## <a name="cautovectorptrm_p"></a><a name="m_p"></a>CAutoVectorPtr::m_p

Die Zeigerdatenmembervariable.

```
T* m_p;
```

### <a name="remarks"></a>Bemerkungen

Diese Membervariable enthält die Zeigerinformationen.

## <a name="cautovectorptroperator-"></a><a name="operator_eq"></a>CAutoVectorPtr::Operator =

Der Zuweisungsoperator.

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Ein Zeiger.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf einen **\< CAutoVectorPtr T >** zurück.

### <a name="remarks"></a>Bemerkungen

Der Zuweisungsoperator trennt `CAutoVectorPtr` das Objekt von einem beliebigen aktuellen Zeiger und fügt den neuen Zeiger *p*an seiner Stelle an.

## <a name="cautovectorptroperator-t-"></a><a name="operator_t__star"></a>CAutoVectorPtr::Operator T *

Der Gussoperator.

```
operator T*() const throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt einen Zeiger auf den in der Klassenvorlage definierten Objektdatentyp zurück.

## <a name="see-also"></a>Siehe auch

[CAutoPtr-Klasse](../../atl/reference/cautoptr-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
