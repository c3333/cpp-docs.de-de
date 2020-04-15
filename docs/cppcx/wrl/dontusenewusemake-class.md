---
title: DontUseNewUseMake-Klasse
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
ms.openlocfilehash: ae67373b4f2f2d4a199b939b06e6f526f1365446
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371555"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake-Klasse

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Bemerkungen

Verhindert die `new` `RuntimeClass`Verwendung des Operators in . Daher müssen Sie stattdessen die [Funktion Erstellen](make-function.md) verwenden.

## <a name="members"></a>Member

### <a name="public-operators"></a>Öffentliche Operatoren

Name                                             | BESCHREIBUNG
------------------------------------------------ | ---------------------------------------------------------------------------
[DontUseNewUseMake::operator neu](#operator-new) | Überlastet Operator `new` und verhindert, dass `RuntimeClass`er in verwendet wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`DontUseNewUseMake`

## <a name="requirements"></a>Anforderungen

**Header:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="dontusenewusemakeoperator-new"></a><a name="operator-new"></a>DontUseNewUseMake::operator neu

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>Parameter

*__unnamed0*<br/>
Ein unbenannter Parameter, der die Anzahl der zuzuweisenden Bytes an Speicher angibt.

*Platzierung*<br/>
Der typ, der zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Bietet eine Möglichkeit, zusätzliche Argumente zu `new`übergeben, wenn Sie den Operator überladen.

### <a name="remarks"></a>Bemerkungen

Überlastet Operator `new` und verhindert, dass `RuntimeClass`er in verwendet wird.
