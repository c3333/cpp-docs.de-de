---
title: ICommandTextImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- ICommandText
- GetCommandText
- ICommandTextImpl.GetCommandText
- ICommandTextImpl::GetCommandText
- ATL::ICommandTextImpl::m_strCommandText
- ICommandTextImpl<T>::m_strCommandText
- m_strCommandText
- ICommandTextImpl.m_strCommandText
- ICommandTextImpl::m_strCommandText
- ATL::ICommandTextImpl<T>::m_strCommandText
- ATL.ICommandTextImpl.m_strCommandText
- ICommandTextImpl.SetCommandText
- ICommandTextImpl::SetCommandText
- SetCommandText
helpviewer_keywords:
- ICommandText class
- GetCommandText method
- m_strCommandText
- SetCommandText method
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
ms.openlocfilehash: 7d31933b162a74db31bdd3c65dc68e396a3896c4
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501718"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl-Klasse

Stellt eine Implementierung für die [ICommandText](/previous-versions/windows/desktop/ms714914(v=vs.85)) -Schnittstelle bereit.

## <a name="syntax"></a>Syntax

```cpp
template <class T >
class ATL_NO_VTABLE ICommandTextImpl
   : public ICommandImpl<T, ICommandText>
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die von abgeleitete Befehls Klasse `ICommandTextImpl` .

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** altdb. h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Schnittstellenmethoden

| Name | Beschreibung |
|-|-|
|[GetCommandText](#getcommandtext)|Gibt den Textbefehl zurück, der beim letzten Aufrufen von [SetCommandText](#setcommandtext)festgelegt wurde.|
|[SetCommandText](#setcommandtext)|Legt den Befehls Text fest und ersetzt den vorhandenen Befehls Text.|

### <a name="data-members"></a>Datenelemente

| Name | Beschreibung |
|-|-|
|[m_strCommandText](#strcommandtext)|Speichert den Befehls Text.|

## <a name="remarks"></a>Bemerkungen

Eine erforderliche Schnittstelle für Befehle.

## <a name="icommandtextimplgetcommandtext"></a><a name="getcommandtext"></a> ICommandTextImpl:: getcommandtext

Gibt den Textbefehl zurück, der beim letzten Aufrufen von [SetCommandText](#setcommandtext)festgelegt wurde.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(GetCommandText)(GUID * pguidDialect,
   LPOLESTR * ppwszCommand);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [ICommandText:: getcommandtext](/previous-versions/windows/desktop/ms709825(v=vs.85)) in der *OLE DB Programmierer-Referenz*. Der *pguiddialekt* -Parameter wird standardmäßig ignoriert.

## <a name="icommandtextimplsetcommandtext"></a><a name="setcommandtext"></a> ICommandTextImpl:: SetCommandText

Legt den Befehls Text fest und ersetzt den vorhandenen Befehls Text.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect,
   LPCOLESTR pwszCommand);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [ICommandText:: SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="icommandtextimplm_strcommandtext"></a><a name="strcommandtext"></a> ICommandTextImpl:: m_strCommandText

Speichert die Zeichenfolge für den Befehls Text.

### <a name="syntax"></a>Syntax

```cpp
CComBSTR m_strCommandText;
```

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur der OLE DB-Anbieter Vorlage](../../data/oledb/ole-db-provider-template-architecture.md)
