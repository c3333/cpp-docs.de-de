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
ms.openlocfilehash: 4a4978401ba90e3a7a91ac40cc1b0668adf12ee8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210716"
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
Das Sitzungs Objekt, das von `IDBCreateCommandImpl`abgeleitet ist.

*CommandClass*<br/>
Ihre Befehls Klasse.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldb.h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Schnittstellenmethoden

|||
|-|-|
|[CreateCommand](#createcommand)|Erstellt einen neuen Befehl.|

## <a name="remarks"></a>Bemerkungen

Eine optionale Schnittstelle für das Sitzungs Objekt zum Abrufen eines neuen Befehls.

## <a name="idbcreatecommandimplcreatecommand"></a><a name="createcommand"></a>Idbkreatecommandimpl:: up Command

Erstellt einen neuen Befehl und gibt die angeforderte Schnittstelle zurück.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppvCommand);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie in der *OLE DB Programmierer-Referenz*unter [idbkreatecommand:: kreatecommand](/previous-versions/windows/desktop/ms709772(v=vs.85)) .

Einige Parameter entsprechen *OLE DB Programmier Verweis* Parametern unterschiedlicher Namen, die in `IDBCreateCommand::CreateCommand`beschrieben werden:

|Parameter für OLE DB Vorlage|*Verweis Parameter für OLE DB Programmierer*|
|--------------------------------|------------------------------------------------|
|*ppvcommand*|*ppcommand*|

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)
