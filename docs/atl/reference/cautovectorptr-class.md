---
title: Cautovectorptr-Klasse
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
ms.openlocfilehash: 65d37396b02d2c11c758915b201eef09cf1935b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226645"
---
# <a name="cautovectorptr-class"></a>Cautovectorptr-Klasse

Diese Klasse stellt ein intelligentes Zeiger Objekt mithilfe von Vector New-und DELETE-Operatoren dar.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

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

|Name|Beschreibung|
|----------|-----------------|
|[Cautovector PTR:: cautovector](#cautovectorptr)|Der Konstruktor.|
|[Cautovector PTR:: ~ cautovector PTR](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Cautovector PTR:: zuordnen](#allocate)|Verwenden Sie diese Methode, um den Arbeitsspeicher zuzuordnen, der für das Array von-Objekten benötigt wird, auf die von `CAutoVectorPtr`|
|[Cautovector PTR:: Attach](#attach)|Ruft diese Methode auf, um den Besitz eines vorhandenen Zeigers zu übernehmen.|
|[Cautovector PTR::D Etach](#detach)|Ruft diese Methode auf, um den Besitz eines Zeigers freizugeben.|
|[Cautovector PTR:: Free](#free)|Mit dieser Methode können Sie ein Objekt löschen, auf das von verwiesen wird `CAutoVectorPtr` .|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[Cautovector PTR:: Operator T *](#operator_t__star)|Der Umwandlungs Operator.|
|[Cautovector PTR:: Operator =](#operator_eq)|Der Zuweisungs Operator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[Cautovector PTR:: m_p](#m_p)|Die Zeiger Datenelement Variable.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt Methoden zum Erstellen und Verwalten eines intelligenten Zeigers bereit, der zum Schutz vor Speicher Verlusten beiträgt, indem Ressourcen automatisch freigegeben werden, wenn Sie den Gültigkeitsbereich verlassen. `CAutoVectorPtr`ähnelt `CAutoPtr` , der einzige Unterschied darin, dass `CAutoVectorPtr` [Vector New&#91;&#93;](../../standard-library/new-operators.md#op_new_arr) und [Vector DELETE&#91;&#93;](../../standard-library/new-operators.md#op_delete_arr) verwendet, um Speicher anstelle der C++ **`new`** -und-Operatoren zuzuordnen und freizugeben **`delete`** . Weitere Informationen finden Sie unter [cautovectorptrelementmerkmalen](../../atl/reference/cautovectorptrelementtraits-class.md) , wenn Auflistungs Klassen von `CAutoVectorPtr` erforderlich sind.

Ein Beispiel für die Verwendung einer intelligenten Zeiger Klasse finden Sie unter [cautoptr](../../atl/reference/cautoptr-class.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="cautovectorptrallocate"></a><a name="allocate"></a>Cautovector PTR:: zuordnen

Verwenden Sie diese Methode, um den Arbeitsspeicher zuzuordnen, der für das Array von-Objekten benötigt wird, auf die von `CAutoVectorPtr`

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>Parameter

*nelements*<br/>
Die Anzahl der Elemente im Array.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Arbeitsspeicher erfolgreich zugewiesen wurde, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Fehler auf, wenn die [cautovector PTR:: m_p](#m_p) Member-Variable derzeit auf einen vorhandenen Wert verweist. Das heißt, es ist nicht gleich NULL.

## <a name="cautovectorptrattach"></a><a name="attach"></a>Cautovector PTR:: Attach

Ruft diese Methode auf, um den Besitz eines vorhandenen Zeigers zu übernehmen.

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parameter

*cker*<br/>
Das `CAutoVectorPtr` Objekt übernimmt den Besitz dieses Zeigers.

### <a name="remarks"></a>Bemerkungen

Wenn ein- `CAutoVectorPtr` Objekt in den Besitz eines Zeigers übergeht, werden der Zeiger und alle zugeordneten Daten automatisch gelöscht, wenn der Gültigkeitsbereich verlässt. Wenn [cautovector PTR::D Etach](#detach) aufgerufen wird, erhält der Programmierer erneut die Verantwortung für die Freigabe zugeordneter Ressourcen.

In Debugbuilds tritt ein Fehler auf, wenn die [cautovector PTR:: m_p](#m_p) Member-Variable derzeit auf einen vorhandenen Wert verweist. Das heißt, es ist nicht gleich NULL.

## <a name="cautovectorptrcautovectorptr"></a><a name="cautovectorptr"></a>Cautovector PTR:: cautovector

Der Konstruktor.

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Parameter

*cker*<br/>
Ein vorhandener-Zeiger.

### <a name="remarks"></a>Bemerkungen

Das `CAutoVectorPtr` Objekt kann mit einem vorhandenen Zeiger erstellt werden. in diesem Fall überträgt es den Besitz des Zeigers.

## <a name="cautovectorptrcautovectorptr"></a><a name="dtor"></a>Cautovector PTR:: ~ cautovector PTR

Der Destruktor.

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugeordneten Ressourcen frei. Ruft [cautovectorptr:: Free](#free)auf.

## <a name="cautovectorptrdetach"></a><a name="detach"></a>Cautovector PTR::D Etach

Ruft diese Methode auf, um den Besitz eines Zeigers freizugeben.

```
T* Detach() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt eine Kopie des Zeigers zurück.

### <a name="remarks"></a>Bemerkungen

Gibt den Besitz eines Zeigers frei, legt die [cautovector PTR:: m_p](#m_p) -Member-Variable auf NULL fest und gibt eine Kopie des Zeigers zurück. Nachdem aufgerufen `Detach` wurde, ist es dem Programmierer überlassen, zugeordnete Ressourcen freizugeben, über die das `CAutoVectorPtr` Objekt möglicherweise bereits verantwortlich ist.

## <a name="cautovectorptrfree"></a><a name="free"></a>Cautovector PTR:: Free

Mit dieser Methode können Sie ein Objekt löschen, auf das von verwiesen wird `CAutoVectorPtr` .

```cpp
void Free() throw();
```

### <a name="remarks"></a>Bemerkungen

Das Objekt, auf das verweist `CAutoVectorPtr` , wird freigegeben, und die [cautovectorptr:: m_p](#m_p) -Member-Variable wird auf NULL festgelegt.

## <a name="cautovectorptrm_p"></a><a name="m_p"></a>Cautovector PTR:: m_p

Die Zeiger Datenelement Variable.

```
T* m_p;
```

### <a name="remarks"></a>Bemerkungen

Diese Member-Variable enthält die Zeiger Informationen.

## <a name="cautovectorptroperator-"></a><a name="operator_eq"></a>Cautovector PTR:: Operator =

Der Zuweisungs Operator.

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Parameter

*cker*<br/>
Ein-Zeiger.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf einen **cautovector \< T > **zurück.

### <a name="remarks"></a>Bemerkungen

Der Zuweisungs Operator trennt das `CAutoVectorPtr` Objekt von allen aktuellen Zeigern und fügt den neuen Zeiger *p*an seiner Stelle an.

## <a name="cautovectorptroperator-t-"></a><a name="operator_t__star"></a>Cautovector PTR:: Operator T *

Der Umwandlungs Operator.

```
operator T*() const throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt einen Zeiger auf den in der Klassen Vorlage definierten Objekt Datentyp zurück.

## <a name="see-also"></a>Siehe auch

[Cautoptr-Klasse](../../atl/reference/cautoptr-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
