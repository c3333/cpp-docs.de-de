---
title: Iaxwinambientdispatchex-Schnittstelle
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
ms.openlocfilehash: 3359c17996eb78c3249abc83ff2d439381f209fe
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352985"
---
# <a name="iaxwinambientdispatchex-interface"></a>Iaxwinambientdispatchex-Schnittstelle

Diese Schnittstelle implementiert zusätzliche Ambient-Eigenschaften für ein gehosteter-Steuerelement.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|Name|BESCHREIBUNG|
|-|-|
|[Setambientdispatch](#setambientdispatch)|Diese Methode wird aufgerufen, um die standardmäßige Ambient-Eigenschaften Schnittstelle durch eine benutzerdefinierte Schnittstelle zu ergänzen.|

## <a name="remarks"></a>Hinweise

Fügen Sie diese Schnittstelle in ATL-Anwendungen ein, die statisch mit ATL-und Host-ActiveX-Steuerelementen verknüpft sind, insbesondere ActiveX-Steuerelemente mit Ambient-Eigenschaften. Wenn Sie diese Schnittstelle nicht einschließen, wird diese Assertion generiert: "haben Sie vergessen, die LIBID an CComModule:: init zu übergeben"

Diese Schnittstelle wird durch die ActiveX-Steuerelemente des ATL-Steuer Elements verfügbar gemacht. Wird von [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)abgeleitet und `IAxWinAmbientDispatchEx` Fügt eine Methode hinzu, mit der Sie die von ATL bereitgestellte Ambient-Eigenschaften Schnittstelle mit einem ihrer eigenen ergänzen können.

<xref:System.Windows.Forms.AxHost> versucht, Typinformationen über `IAxWinAmbientDispatch` und `IAxWinAmbientDispatchEx` aus der Typbibliothek, die den Code enthält, zu laden.

Wenn Sie mit ATL90.dll verknüpfen, lädt **AxHost** die Typinformationen aus der Typbibliothek in der dll.

Weitere Informationen finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) .

## <a name="requirements"></a>Requirements (Anforderungen)

Die Definition dieser Schnittstelle ist in einer Reihe von Formularen verfügbar, wie in der folgenden Tabelle dargestellt.

|Definitionstyp|Datei|
|---------------------|----------|
|IDL|atliface. idl|
|Typbibliothek|ATL.dll|
|C++|atliface. h (auch in "atlbase. h" enthalten)|

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a> Iaxwinambientdispatchex:: setambientdispatch

Diese Methode wird aufgerufen, um die standardmäßige Ambient-Eigenschaften Schnittstelle durch eine benutzerdefinierte Schnittstelle zu ergänzen.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parameter

*pdispatch*<br/>
Ein Zeiger auf die neue-Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Wenn `SetAmbientDispatch` mit einem Zeiger auf eine neue Schnittstelle aufgerufen wird, wird diese neue Schnittstelle verwendet, um alle Eigenschaften oder Methoden aufzurufen, die vom gehosteten Steuerelement angefordert werden, wenn diese Eigenschaften nicht bereits von [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)bereitgestellt werden.

## <a name="see-also"></a>Weitere Informationen

[IAxWinAmbientDispatch-Schnittstelle](../../atl/reference/iaxwinambientdispatch-interface.md)
