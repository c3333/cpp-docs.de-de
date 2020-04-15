---
title: FactoryCache-Struktur
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
- module/Microsoft::WRL::Details::FactoryCache::cookie
- module/Microsoft::WRL::Details::FactoryCache::factory
helpviewer_keywords:
- Microsoft::WRL::Details::FactoryCache structure
- Microsoft::WRL::Details::FactoryCache::cookie data member
- Microsoft::WRL::Details::FactoryCache::factory data member
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
ms.openlocfilehash: 507d35179b9fa86399e56b18171800f41eaf1f10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371493"
---
# <a name="factorycache-structure"></a>FactoryCache-Struktur

Unterstützt die Windows Runtime C++-Vorlagenbibliotheksinfrastruktur und ist nicht für die direkte Verwendung aus Ihrem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>Bemerkungen

Enthält den Speicherort einer Klassenfactory und einen Wert, der ein registriertes wrt- oder COM-Klassenobjekt identifiziert.

## <a name="members"></a>Member

### <a name="public-data-members"></a>Öffentliche Datenmember

Name                              | BESCHREIBUNG
--------------------------------- | ------------------------------------------------------------------------------------------------------------------------------
[FactoryCache::Cookie](#cookie)   | Enthält einen Wert, der ein registriertes Windows-Runtime- oder COM-Klassenobjekt identifiziert und später zum Aufheben der Registrierung des Objekts verwendet wird.
[FactoryCache::Fabrik](#factory) | Verweist auf eine Windows-Runtime- oder COM-Klassenfactory.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`FactoryCache`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="factorycachecookie"></a><a name="cookie"></a>FactoryCache::Cookie

Unterstützt die Windows Runtime C++-Vorlagenbibliotheksinfrastruktur und ist nicht für die direkte Verwendung aus Ihrem Code vorgesehen.

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

### <a name="remarks"></a>Bemerkungen

Enthält einen Wert, der ein registriertes Windows-Runtime- oder COM-Klassenobjekt identifiziert und später zum Aufheben der Registrierung des Objekts verwendet wird.

## <a name="factorycachefactory"></a><a name="factory"></a>FactoryCache::Fabrik

Unterstützt die Windows Runtime C++-Vorlagenbibliotheksinfrastruktur und ist nicht für die direkte Verwendung aus Ihrem Code vorgesehen.

```cpp
IUnknown* factory;
```

### <a name="remarks"></a>Bemerkungen

Verweist auf eine Windows-Runtime- oder COM-Klassenfactory.
