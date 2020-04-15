---
title: Platform::SizeT-Wertklasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
ms.openlocfilehash: 5add9212dc2655bc37cd357741073f855b009bde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322158"
---
# <a name="platformsizet-value-class"></a>Platform::SizeT-Wertklasse

Stellt die Größe eines Objekts dar. SizeT ist ein Datentyp ohne Vorzeichen.

## <a name="syntax"></a>Syntax

```cpp
public ref class SizeT sealed : ValueType
```

### <a name="members"></a>Member

|Member|BESCHREIBUNG|
|------------|-----------------|
|[SizeT::SizeT-Konstruktor](#ctor)|Initialisiert eine neue Instanz der Klasse mit dem angegebenen Wert.|

### <a name="requirements"></a>Anforderungen

**Mindestens unterstützter Client:** Windows 8

**Minimal unterstützter Server:** Windows Server 2012

**Namespace:** Platform

**Metadaten:** platform.winmd

## <a name="sizetsizet-constructor"></a><a name="ctor"></a>SizeT::SizeT-Konstruktor

Initialisiert eine neue Instanz von SizeT mit dem angegebenen Wert.

### <a name="syntax"></a>Syntax

```cpp
SizeT( uint32 value1 );   SizeT( void* value2 );
```

### <a name="parameters"></a>Parameter

*value1*<br/>
Ein nicht signierter 32-Bit-Wert.

*value2*<br/>
Zeiger auf einen nicht signierten 32-Bit-Wert.

## <a name="see-also"></a>Siehe auch

[Plattformnamespace](../cppcx/platform-namespace-c-cx.md)
