---
title: Platform::ValueType-Klasse
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ValueType::ToString
helpviewer_keywords:
- Platform::ValueType Class
ms.assetid: 79aa8754-b140-4974-a5b1-be046938a10a
ms.openlocfilehash: f4ce34fa3f197424833d34bdb866712d412e69c3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846549"
---
# <a name="platformvaluetype-class"></a>Platform::ValueType-Klasse

Die Basisklasse für Instanzen von Werttypen.

## <a name="syntax"></a>Syntax

```cpp
public ref class ValueType : Object
```

## <a name="public-methods"></a>Öffentliche Methoden

| Name | Beschreibung |
|--|--|
| [ValueType::-Zeichenfolge](#tostring) | Gibt eine Zeichenfolgendarstellung des Objekts zurück. Geerbt von [Platform:: Object](../cppcx/platform-object-class.md). |

### <a name="remarks"></a>Bemerkungen

Die ValueType-Klasse wird zum Erstellen von Werttypen verwendet. „ValueType“ ist von „Object“ abgeleitet, die über Basismember verfügt. Der Compiler trennt jedoch diese Basismember von den Werttypen, die aus der ValueType-Klasse abgeleitet sind. Der Compiler fügt die Basismember wieder an, wenn ein Werttyp mittels Boxing konvertiert wird.

### <a name="requirements"></a>Requirements (Anforderungen)

**Mindestens unterstützter Client:** Windows 8

**Mindestens unterstützter Server:** Windows Server 2012

**Namespace:** Platform

**Metadaten:** Platform. winmd

## <a name="valuetypetostring-method"></a><a name="tostring"></a> ValueType:: destring-Methode

Gibt eine Zeichenfolgendarstellung des Objekts zurück.

### <a name="syntax"></a>Syntax

```cpp
Platform::String ToString();
```

### <a name="return-value"></a>Rückgabewert

Eine Platform:: String, die den Wert darstellt.

## <a name="see-also"></a>Weitere Informationen

[Plattformnamespace](../cppcx/platform-namespace-c-cx.md)
