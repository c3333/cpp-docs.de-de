---
title: IAxWinAmbientDispatchEx-Schnittstelle
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
ms.openlocfilehash: f4816846801e388619db62998ec979a1100916ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329977"
---
# <a name="iaxwinambientdispatchex-interface"></a>IAxWinAmbientDispatchEx-Schnittstelle

Diese Schnittstelle implementiert zusätzliche Umgebungseigenschaften für ein gehostetes Steuerelement.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[SetAmbientDispatch](#setambientdispatch)|Diese Methode wird aufgerufen, um die standardmäßige Umgebungseigenschaftsschnittstelle durch eine benutzerdefinierte Schnittstelle zu ergänzen.|

## <a name="remarks"></a>Bemerkungen

Schließen Sie diese Schnittstelle in ATL-Anwendungen ein, die statisch mit ATL- und Host-ActiveX-Steuerelementen verknüpft sind, insbesondere ActiveX-Steuerelemente mit Umgebungseigenschaften. Ohne diese Schnittstelle wird diese Assertion generiert: "Haben Sie vergessen, das LIBID an CComModule::Init übergeben"

Diese Schnittstelle wird von ATLs ActiveX-Steuerelementhostingobjekten verfügbar gemacht. Abgeleitet von [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md), `IAxWinAmbientDispatchEx` fügt eine Methode hinzu, mit der Sie die von ATL bereitgestellte Umgebungseigenschaftsschnittstelle um eine eigene eigenschaft ergänzen können.

<xref:System.Windows.Forms.AxHost>versucht, Typinformationen über `IAxWinAmbientDispatch` `IAxWinAmbientDispatchEx` und aus der Typbibliothek zu laden, die den Code enthält.

Wenn Sie eine Verknüpfung mit ATL90.dll herstellen, lädt **AXHost** die Typinformationen aus der Typbibliothek in der DLL.

Weitere Informationen finden Sie unter [Hosting von ActiveX-Steuerelementen unter Verwendung von ATL AXHost.](../../atl/hosting-activex-controls-using-atl-axhost.md)

## <a name="requirements"></a>Anforderungen

Die Definition dieser Schnittstelle ist in einer Reihe von Formen verfügbar, wie in der folgenden Tabelle dargestellt.

|Definitionstyp|Datei|
|---------------------|----------|
|Idl|atliface.idl|
|Typbibliothek|ATL.dll|
|C++|atliface.h (auch in ATLBase.h enthalten)|

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch

Diese Methode wird aufgerufen, um die standardmäßige Umgebungseigenschaftsschnittstelle durch eine benutzerdefinierte Schnittstelle zu ergänzen.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parameter

*pDispatch*<br/>
Zeiger auf die neue Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Wenn `SetAmbientDispatch` mit einem Zeiger auf eine neue Schnittstelle aufgerufen wird, wird diese neue Schnittstelle verwendet, um alle Eigenschaften oder Methoden aufzurufen, die vom gehosteten Steuerelement angefordert werden, wenn diese Eigenschaften nicht bereits von [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)bereitgestellt werden.

## <a name="see-also"></a>Siehe auch

[IAxWinAmbientDispatch-Schnittstelle](../../atl/reference/iaxwinambientdispatch-interface.md)
