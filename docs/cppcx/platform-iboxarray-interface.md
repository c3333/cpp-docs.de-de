---
title: Platform::IBoxArray-Schnittstelle
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IBoxArray
- VCCORLIB/Platform::IBoxArray::Value
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
ms.openlocfilehash: 493770cab092c2bb719d47e5d3a9d6a9f0646489
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444159"
---
# <a name="platformiboxarray-interface"></a>Platform::IBoxArray-Schnittstelle

,`IBoxArray` ist der Wrapper für Arrays von Werttypen, die über die Anwendungsbinärdateischnittstelle (ABI) übergeben werden oder in Auflistungen von `Platform::Object^` -Elementen, wie die in XAML-Steuerelementen, gespeichert werden.

## <a name="syntax"></a>Syntax

```cpp
template <typename T>
interface class IBoxArray
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des geschachtelten Werts in jedem Arrayelement.

### <a name="remarks"></a>Bemerkungen

`IBoxArray` ist der C++/CX Name für `Windows::Foundation::IReferenceArray`.

### <a name="members"></a>Members

Die `IBoxArray` -Schnittstelle erbt von der `IValueType` -Schnittstelle. `IBoxArray` umfasst auch folgende Member:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Wert](#value)|Gibt das nicht geschachtelte Array zurück, das zuvor in dieser `IBoxArray` -Instanz gespeichert wurde.|

## <a name="value"></a>Iboxarray:: Value-Eigenschaft

Gibt den ursprünglich in diesem Objekt gespeicherten Wert zurück.

### <a name="syntax"></a>Syntax

```cpp
property T Value {T get();}
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des geschachtelten Werts.

### <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

Gibt den ursprünglich in diesem Objekt gespeicherten Wert zurück.

### <a name="remarks"></a>Bemerkungen

Ein Beispiel finden Sie unter [Boxing](../cppcx/boxing-c-cx.md).

## <a name="see-also"></a>Weitere Informationen

[Array und WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
