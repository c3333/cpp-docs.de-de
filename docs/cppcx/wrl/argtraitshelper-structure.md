---
title: ArgTraitsHelper-Struktur
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
- event/Microsoft::WRL::Details::ArgTraitsHelper::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraitsHelper structure
- Microsoft::WRL::Details::ArgTraitsHelper::args constant
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
ms.openlocfilehash: 4acbd9fa660f29bbaf209282ff0e90f43621574d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360771"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>Parameter

*TDelegateInterface*<br/>
Eine Delegatschnittstelle.

## <a name="remarks"></a>Bemerkungen

Hilft beim Definieren gemeinsamer Merkmale von Delegatenargumenten.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

Name         | BESCHREIBUNG
------------ | ------------------------------------------------------
`methodType` | Ein Synonym für `decltype(&TDelegateInterface::Invoke)`.
`Traits`     | Ein Synonym für `ArgTraits<methodType>`.

### <a name="public-constants"></a>Öffentliche Konstanten

Name                           | BESCHREIBUNG
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[ArgTraitsHelper::args](#args) | Hilft [ArgTraits::args](#args) zählt die Anzahl der `Invoke` Parameter auf der Methode einer Delegatschnittstelle.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ArgTraitsHelper`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="argtraitshelperargs"></a><a name="args"></a>ArgTraitsHelper::args

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>Bemerkungen

Hilft `ArgTraitsHelper::args` dabei, die Anzahl der `Invoke` Parameter für die Methode einer Delegatschnittstelle beizubehalten.
