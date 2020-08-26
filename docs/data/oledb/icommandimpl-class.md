---
title: ICommandImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- ICommandImpl
- ICommandImpl::Cancel
- Cancel
- ICommandImpl.Cancel
- ICommandImpl::CancelExecution
- ATL::ICommandImpl::CancelExecution
- ATL.ICommandImpl.CancelExecution
- CancelExecution
- ICommandImpl.CancelExecution
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
- ICommandImpl::Execute
- ICommandImpl.Execute
- ICommandImpl::GetDBSession
- GetDBSession
- ICommandImpl.GetDBSession
- ATL.ICommandImpl.ICommandImpl
- ATL::ICommandImpl::ICommandImpl
- ICommandImpl::ICommandImpl
- ICommandImpl.ICommandImpl
- ICommandImpl::m_bCancel
- ICommandImpl.m_bCancel
- m_bCancel
- ATL::ICommandImpl::m_bCancel
- ATL.ICommandImpl.m_bCancel
- ICommandImpl::m_bCancelWhenExecuting
- ICommandImpl.m_bCancelWhenExecuting
- ATL::ICommandImpl::m_bCancelWhenExecuting
- m_bCancelWhenExecuting
- ATL.ICommandImpl.m_bCancelWhenExecuting
- ICommandImpl.m_bIsExecuting
- ATL::ICommandImpl::m_bIsExecuting
- m_bIsExecuting
- ATL.ICommandImpl.m_bIsExecuting
- ICommandImpl::m_bIsExecuting
helpviewer_keywords:
- ICommandImpl class
- Cancel method
- CancelExecution method
- CreateRowset method
- Execute method
- GetDBSession method
- ICommandImpl constructor
- ICommandImpl class, constructor
- m_bCancel
- m_bCancelWhenExecuting
- m_bIsExecuting
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
ms.openlocfilehash: c88554d717888719ad6d805a2871489ce4b0df32
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845587"
---
# <a name="icommandimpl-class"></a>ICommandImpl-Klasse

Stellt die Implementierung für die [ICommand](/previous-versions/windows/desktop/ms709737(v=vs.85)) -Schnittstelle bereit.

## <a name="syntax"></a>Syntax

```cpp
template <class T, class CommandBase = ICommand>
class ATL_NO_VTABLE ICommandImpl : public CommandBase
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die von abgeleitete Klasse `ICommandImpl` .

*CommandBase*<br/>
Eine Befehlsschnittstelle. Der Standardwert ist `ICommand`.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „atldb.h“

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[Abbrechen](#cancel)|Bricht die Ausführung des aktuellen Befehls ab.|
|[CancelExecution](#cancelexecution)|Bricht die Ausführung des aktuellen Befehls ab.|
|[CreateRowset](#createrowset)|Erstellt ein Rowsetobjekt.|
|[Ausführen](#execute)|Führt den Befehl aus.|
|[GetDBSession](#getdbsession)|Gibt einen Schnittstellen Zeiger auf die Sitzung zurück, die den Befehl erstellt hat.|
|[ICommandImpl](#icommandimpl)|Der Konstruktor.|

### <a name="data-members"></a>Datenelemente

| Name | Beschreibung |
|-|-|
|[m_bCancel](#bcancel)|Gibt an, ob der Befehl abgebrochen werden soll.|
|[m_bCancelWhenExecuting](#bcancelwhenexecuting)|Gibt an, ob der Befehl bei der Ausführung abgebrochen werden soll.|
|[m_bIsExecuting](#bisexecuting)|Gibt an, ob der Befehl gerade ausgeführt wird.|

## <a name="remarks"></a>Bemerkungen

Eine erforderliche Schnittstelle für das Befehls Objekt.

## <a name="icommandimplcancel"></a><a name="cancel"></a> ICommandImpl:: Cancel

Bricht die Ausführung des aktuellen Befehls ab.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(Cancel)();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [ICommand:: Cancel](/previous-versions/windows/desktop/ms714402(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="icommandimplcancelexecution"></a><a name="cancelexecution"></a> ICommandImpl:: cancelexecution

Bricht die Ausführung des aktuellen Befehls ab.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CancelExecution();
```

## <a name="icommandimplcreaterowset"></a><a name="createrowset"></a> ICommandImpl:: kreaterowset

Wird von [Execute](../../data/oledb/icommandimpl-execute.md) aufgerufen, um ein einzelnes Rowset zu erstellen.

### <a name="syntax"></a>Syntax

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>Parameter

*RowsetClass*<br/>
Ein Vorlagen Klassenmember, der die Rowsetklasse des Benutzers darstellt. Wird normalerweise vom Assistenten generiert.

*pUnkOuter*<br/>
in Ein Zeiger auf die Steuerungs `IUnknown` Schnittstelle, wenn das Rowset als Teil eines Aggregats erstellt wird; andernfalls ist es NULL.

*riid*<br/>
in Entspricht *riid* in `ICommand::Execute` .

*pparser*<br/>
[in/out] Entspricht *pparameams* in `ICommand::Execute` .

*pcrowsafffiziert*<br/>
Entspricht *pcrowsafffiziert* in `ICommand::Execute` .

*ppRowset*<br/>
[in/out] Entspricht *ppRowset* in `ICommand::Execute` .

*prowsetobj*<br/>
vorgenommen Ein Zeiger auf ein Rowsetobjekt. In der Regel wird dieser Parameter nicht verwendet, kann jedoch verwendet werden, wenn Sie vor der Übergabe an ein COM-Objekt mehr Arbeit an dem Rowset ausführen müssen. Die Lebensdauer von *prowsetobj* wird durch *ppRowset*gebunden.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert. `ICommand::Execute`Eine Liste der typischen Werte finden Sie unter.

### <a name="remarks"></a>Bemerkungen

Um mehr als ein Rowset zu erstellen oder eigene Bedingungen zum Erstellen verschiedener Rowsets anzugeben, platzieren Sie unterschiedliche Aufrufe `CreateRowset` von innerhalb von `Execute` .

Weitere Informationen finden Sie unter [ICommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) in der *OLE DB Programmierer-Referenz.*

## <a name="icommandimplexecute"></a><a name="execute"></a> ICommandImpl:: Execute

Führt den Befehl aus.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Execute(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [ICommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="remarks"></a>Bemerkungen

Die angeforderte ausgehende Schnittstelle ist eine Schnittstelle, die vom Rowsetobjekt abgerufen wird, das diese Funktion erstellt.

`Execute` Ruft " [kreaterowset](../../data/oledb/icommandimpl-createrowset.md)" auf. Überschreiben Sie die Standard Implementierung, um mehr als ein Rowset zu erstellen oder eigene Bedingungen zum Erstellen verschiedener Rowsets anzugeben.

## <a name="icommandimplgetdbsession"></a><a name="getdbsession"></a> ICommandImpl:: getdbsession

Gibt einen Schnittstellen Zeiger auf die Sitzung zurück, die den Befehl erstellt hat.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (GetDBSession) (REFIID riid,
   IUnknown** ppSession);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [ICommand:: getdbsession](/previous-versions/windows/desktop/ms719622(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="remarks"></a>Bemerkungen

Nützlich zum Abrufen von Eigenschaften aus der Sitzung.

## <a name="icommandimplicommandimpl"></a><a name="icommandimpl"></a> ICommandImpl:: ICommandImpl

Der Konstruktor.

### <a name="syntax"></a>Syntax

```cpp
ICommandImpl();
```

## <a name="icommandimplm_bcancel"></a><a name="bcancel"></a> ICommandImpl:: m_bCancel

Gibt an, ob der Befehl abgebrochen wird.

### <a name="syntax"></a>Syntax

```cpp
unsigned m_bCancel:1;
```

### <a name="remarks"></a>Bemerkungen

Sie können diese Variable in der `Execute` -Methode der Befehls Klasse abrufen und entsprechend abbrechen.

## <a name="icommandimplm_bcancelwhenexecuting"></a><a name="bcancelwhenexecuting"></a> ICommandImpl:: m_bCancelWhenExecuting

Gibt an, ob der Befehl bei der Ausführung abgebrochen werden kann.

### <a name="syntax"></a>Syntax

```cpp
unsigned m_bCancelWhenExecuting:1;
```

### <a name="remarks"></a>Bemerkungen

Der Standardwert **`true`** ist (kann abgebrochen werden).

## <a name="icommandimplm_bisexecuting"></a><a name="bisexecuting"></a> ICommandImpl:: m_bIsExecuting

Gibt an, ob der Befehl gerade ausgeführt wird.

### <a name="syntax"></a>Syntax

```cpp
unsigned m_bIsExecuting:1;
```

### <a name="remarks"></a>Bemerkungen

Die- `Execute` Methode Ihrer Command-Klasse kann diese Variable auf festlegen **`true`** .

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur der OLE DB-Anbieter Vorlage](../../data/oledb/ole-db-provider-template-architecture.md)
