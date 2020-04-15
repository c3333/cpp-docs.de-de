---
title: CInterfaceList-Klasse
ms.date: 11/04/2016
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
ms.openlocfilehash: 0a7fd781c63e4ea084cf078e49fc9efb9cfa2d85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326781"
---
# <a name="cinterfacelist-class"></a>CInterfaceList-Klasse

Diese Klasse stellt Methoden bereit, die beim Erstellen einer Liste von COM-Schnittstellenzeigern nützlich sind.

## <a name="syntax"></a>Syntax

```
template<class I, const IID* piid =& __uuidof(I)>
class CInterfaceList
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>Parameter

*Ⅰ*<br/>
Eine COM-Schnittstelle, die den Typ des zu speichernden Zeigers angibt.

*piid*<br/>
Ein Zeiger auf die IID von *I*.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInterfaceList::CInterfaceList](#cinterfacelist)|Der Konstruktor für die Schnittstellenliste.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt einen Konstruktor und abgeleitete Methoden zum Erstellen einer Liste von COM-Schnittstellenzeigern bereit. Verwenden Sie [CInterfaceArray,](../../atl/reference/cinterfacearray-class.md) wenn ein Array erforderlich ist.

Weitere Informationen finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CAtlList](../../atl/reference/catllist-class.md)

`CInterfaceList`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="cinterfacelistcinterfacelist"></a><a name="cinterfacelist"></a>CInterfaceList::CInterfaceList

Der Konstruktor für die Schnittstellenliste.

```
CInterfaceList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parameter

*nBlockSize*<br/>
Die Blockgröße mit einem Standardwert von 10.

### <a name="remarks"></a>Bemerkungen

Die Blockgröße ist ein Maß für die Speichermenge, die zugewiesen wird, wenn ein neues Element erforderlich ist. Größere Blockgrößen reduzieren Aufrufe von Speicherzuweisungsroutinen, verwenden jedoch mehr Ressourcen.

## <a name="see-also"></a>Siehe auch

[CAtlList-Klasse](../../atl/reference/catllist-class.md)<br/>
[CComQIPtr-Klasse](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits-Klasse](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
