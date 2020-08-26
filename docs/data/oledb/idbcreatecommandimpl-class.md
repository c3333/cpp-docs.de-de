---
title: IDBCreateCommandImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- IDBCreateCommandImpl::CreateCommand
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
ms.openlocfilehash: b7b658b2b365eb84a39ae94cef7c77e18d7bd4a0
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845548"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl-Klasse

Stellt eine Implementierung der [idbkreatecommand](/previous-versions/windows/desktop/ms711625(v=vs.85)) -Schnittstelle bereit.

## <a name="syntax"></a>Syntax

```cpp
template <class T, class CommandClass >
class ATL_NO_VTABLE IDBCreateCommandImpl
   : public IDBCreateCommand
```

### <a name="parameters"></a>Parameter

*T*<br/>
Das Sitzungs Objekt, das von abgeleitet wird `IDBCreateCommandImpl` .

*CommandClass*<br/>
Ihre Befehls Klasse.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „atldb.h“

## <a name="members"></a>Member

### <a name="interface-methods"></a>Schnittstellenmethoden

| Name | Beschreibung |
|-|-|
|[CreateCommand](#createcommand)|Erstellt einen neuen Befehl.|

## <a name="remarks"></a>Bemerkungen

Eine optionale Schnittstelle für das Sitzungs Objekt zum Abrufen eines neuen Befehls.

## <a name="idbcreatecommandimplcreatecommand"></a><a name="createcommand"></a> Idbkreatecommandimpl:: up Command

Erstellt einen neuen Befehl und gibt die angeforderte Schnittstelle zurück.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppvCommand);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie in der *OLE DB Programmierer-Referenz*unter [idbkreatecommand:: kreatecommand](/previous-versions/windows/desktop/ms709772(v=vs.85)) .

Einige Parameter entsprechen *OLE DB Programmier Verweis* Parametern mit unterschiedlichen Namen, die in beschrieben werden `IDBCreateCommand::CreateCommand` :

|Parameter für OLE DB Vorlage|*Verweis Parameter für OLE DB Programmierer*|
|--------------------------------|------------------------------------------------|
|*ppvcommand*|*ppcommand*|

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur der OLE DB-Anbieter Vorlage](../../data/oledb/ole-db-provider-template-architecture.md)
