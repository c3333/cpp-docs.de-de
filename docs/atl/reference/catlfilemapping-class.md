---
title: CAtlFileMapping-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: ca46ccdacf5ea24f1de26cdc75bf808c4ecfaa40
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318958"
---
# <a name="catlfilemapping-class"></a>CAtlFileMapping-Klasse

Diese Klasse stellt eine Speicherzuordnungsdatei dar, die den Methoden von [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)einen umwandlungsoperator hinzufügt.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der Daten, die für den Umwandlungsoperator verwendet werden.

## <a name="members"></a>Member

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlFileMapping::operator T*](#operator_t_star)|Ermöglicht die `CAtlFileMapping` implizite `T*`Konvertierung von Objekten in .|

## <a name="remarks"></a>Bemerkungen

Diese Klasse fügt einen einzelnen Umwandlungsoperator hinzu, um die implizite Konvertierung von `CAtlFileMapping` Objekten in zu `T*`ermöglichen. Andere Member werden von der Basisklasse [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)bereitgestellt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlfile.h

## <a name="catlfilemappingoperator-t"></a><a name="operator_t_star"></a>CAtlFileMapping::operator T*

Ermöglicht die `CAtlFileMapping` implizite `T*`Konvertierung von Objekten in .

```
operator T*() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt `T*` einen Zeiger auf den Anfang der Speicherzuordnungsdatei zurück.

### <a name="remarks"></a>Bemerkungen

Ruft [CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) auf und interpretiert den `T*` zurückgegebenen Zeiger als einen, wobei *T* der Typ ist, der als Vorlagenparameter dieser Klasse verwendet wird.

## <a name="see-also"></a>Siehe auch

[CAtlFileMappingBase-Klasse](../../atl/reference/catlfilemappingbase-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
