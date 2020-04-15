---
title: IPropertyNotifySinkCP-Klasse
ms.date: 11/04/2016
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
ms.openlocfilehash: c6d98bf5a6dfe5566839eb22bcd2bab2a9c28e4d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329609"
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP-Klasse

Diese Klasse macht die [IPropertyNotifySink-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) als ausgehende Schnittstelle für ein verbindendes Objekt verfügbar.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IPropertyNotifySinkCP`abgeleitet von .

*Cdv*<br/>
Eine Klasse, die die Verbindungen zwischen einem Verbindungspunkt und seinen Senken verwaltet. Der Standardwert ist [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), der unbegrenzte Verbindungen zulässt. Sie können auch [CComUnkArray](../../atl/reference/ccomunkarray-class.md)verwenden, das eine feste Anzahl von Verbindungen angibt.

## <a name="remarks"></a>Bemerkungen

`IPropertyNotifySinkCP`erbt alle Methoden über seine Basisklasse [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).

Die [IPropertyNotifySink-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) ermöglicht es einem Senkenobjekt, Benachrichtigungen über Eigenschaftenänderungen zu empfangen. Die `IPropertyNotifySinkCP` Klasse macht diese Schnittstelle als ausgehende Schnittstelle für ein verbindendes Objekt verfügbar. Der Client muss `IPropertyNotifySink` die Methoden auf der Senke implementieren.

Leiten Sie Ihre `IPropertyNotifySinkCP` Klasse ab, wenn Sie einen `IPropertyNotifySink` Verbindungspunkt erstellen möchten, der die Schnittstelle darstellt.

Weitere Informationen zur Verwendung von Verbindungspunkten in ATL finden Sie im Artikel [Verbindungspunkte](../../atl/atl-connection-points.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="see-also"></a>Siehe auch

[IConnectionPointImpl-Klasse](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[IConnectionPointContainerImpl-Klasse](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
