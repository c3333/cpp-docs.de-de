---
title: IObjectSafetyImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl::GetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::SetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::m_dwCurrentSafety
helpviewer_keywords:
- controls [ATL], safe
- safe for scripting and initialization (controls)
- IObjectSafety, ATL implementation
- IObjectSafetyImpl class
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
ms.openlocfilehash: 6eee7585bc3c5587e106ab6b0cefb4b7129df59f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329653"
---
# <a name="iobjectsafetyimpl-class"></a>IObjectSafetyImpl-Klasse

Diese Klasse stellt eine `IObjectSafety` Standardimplementierung der Schnittstelle bereit, damit ein Client die Sicherheitsstufen eines Objekts abrufen und festlegen kann.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class T,DWORD dwSupportedSafety>
class IObjectSafetyImpl
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IObjectSafetyImpl`abgeleitet von .

*dwSupportedSafety*<br/>
Gibt die unterstützten Sicherheitsoptionen für das Steuerelement an. Es kann sich um einen der folgenden Werte handeln:

- INTERFACESAFE_FOR_UNTRUSTED_CALLER Die durch den Parameter `riid` [SetInterfaceSafetyOptions](#setinterfacesafetyoptions) identifizierte Schnittstelle sollte für die Skripterstellung sicher gemacht werden.

- INTERFACESAFE_FOR_UNTRUSTED_DATA Die durch `SetInterfaceSafetyOptions` den `riid` Parameter identifizierte Schnittstelle sollte während der Initialisierung für nicht vertrauenswürdige Daten sicher gemacht werden.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|Ruft die vom Objekt unterstützten Sicherheitsoptionen sowie die derzeit für das Objekt festgelegten Sicherheitsoptionen ab.|
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|Macht das Objekt sicher für die Initialisierung oder Skripterstellung.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IObjectSafetyImpl::m_dwCurrentSafety](#m_dwcurrentsafety)|Speichert das aktuelle Sicherheitsniveau des Objekts.|

## <a name="remarks"></a>Bemerkungen

Die `IObjectSafetyImpl` Klasse stellt `IObjectSafety`eine Standardimplementierung von bereit. Die `IObjectSafety` Schnittstelle ermöglicht es einem Client, die Sicherheitsstufen eines Objekts abzurufen und festzulegen. Beispielsweise kann ein Webbrowser `IObjectSafety::SetInterfaceSafetyOptions` aufrufen, um ein Steuerelement für die Initialisierung oder sicher für Skripts zu machen.

Beachten Sie, [IMPLEMENTED_CATEGORY](category-macros.md#implemented_category) dass die Verwendung des IMPLEMENTED_CATEGORY-Makros mit den CATID_SafeForScripting- und CATID_SafeForInitializing Komponentenkategorien eine alternative Möglichkeit bietet, anzugeben, dass eine Komponente sicher ist.

**Verwandte Artikel** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Erstellen eines [ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IObjectSafety`

`IObjectSafetyImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="iobjectsafetyimplgetinterfacesafetyoptions"></a><a name="getinterfacesafetyoptions"></a>IObjectSafetyImpl::GetInterfaceSafetyOptions

Ruft die vom Objekt unterstützten Sicherheitsoptionen sowie die derzeit für das Objekt festgelegten Sicherheitsoptionen ab.

```
HRESULT GetInterfaceSafetyOptions(
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```

### <a name="remarks"></a>Bemerkungen

Die Implementierung gibt die entsprechenden Werte für jede Schnittstelle `IUnknown::QueryInterface`zurück, die von der Implementierung des Objekts unterstützt wird.

> [!IMPORTANT]
> Jedes Objekt, `IObjectSafety` das unterstützt, ist für seine eigene Sicherheit und für jedes von ihm delegierte Objekt verantwortlich. Der Programmierer muss Probleme berücksichtigen, die sich aus der Ausführung von Code im Kontext des Benutzers, der standortübergreifenden Skripterstellung und der durchführung geeigneter Zonenprüfungen ergeben.

Siehe [IObjectSafety::GetInterfaceSafetyOptions](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768223\(v=vs.85\)) im Windows SDK.

## <a name="iobjectsafetyimplm_dwcurrentsafety"></a><a name="m_dwcurrentsafety"></a>IObjectSafetyImpl::m_dwCurrentSafety

Speichert das aktuelle Sicherheitsniveau des Objekts.

```
DWORD m_dwCurrentSafety;
```

## <a name="iobjectsafetyimplsetinterfacesafetyoptions"></a><a name="setinterfacesafetyoptions"></a>IObjectSafetyImpl::SetInterfaceSafetyOptions

Macht das Objekt sicher für die Initialisierung oder Skripterstellung, indem der [m_dwCurrentSafety-Member](#m_dwcurrentsafety) auf den entsprechenden Wert gesetzt wird.

```
HRESULT SetInterfaceSafetyOptions(
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```

### <a name="remarks"></a>Bemerkungen

Die Implementierung gibt E_NOINTERFACE für jede Schnittstelle zurück, `IUnknown::QueryInterface`die von der Implementierung von unterstützt wird.

> [!IMPORTANT]
> Jedes Objekt, `IObjectSafety` das unterstützt, ist für seine eigene Sicherheit und für jedes von ihm delegierte Objekt verantwortlich. Der Programmierer muss Probleme berücksichtigen, die sich aus der Ausführung von Code im Kontext des Benutzers, der standortübergreifenden Skripterstellung und der durchführung geeigneter Zonenprüfungen ergeben.

Siehe [IObjectSafety::SetInterfaceSafetyOptions](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768225\(v=vs.85\)) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[IObjectSafety-Schnittstelle](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768224\(v=vs.85\))<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
