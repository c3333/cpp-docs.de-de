---
title: Iaxwinhostwindowlic-Schnittstelle
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
ms.openlocfilehash: aca3970d13db53ffa04fe9582bbe9b8db78e820d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423075"
---
# <a name="iaxwinhostwindowlic-interface"></a>Iaxwinhostwindowlic-Schnittstelle

Diese Schnittstelle stellt Methoden zum Bearbeiten eines lizenzierten Steuer Elements und seines Host Objekts bereit.

## <a name="syntax"></a>Syntax

```
interface IAxWinHostWindowLic : IAxWinHostWindow
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|["Kreatecontrollic"](#createcontrollic)|Erstellt ein lizenziertes Steuerelement und fügt es an das Host Objekt an.|
|["Kreatecontrollicex"](#createcontrollicex)|Erstellt ein lizenziertes Steuerelement, fügt es an das Host Objekt an und richtet optional einen Ereignishandler ein.|

## <a name="remarks"></a>Hinweise

`IAxWinHostWindowLic` erbt von [IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) und fügt Methoden hinzu, die die Erstellung von lizenzierten Steuerelementen unterstützen.

Ein Beispiel für die Verwendung der Member dieser Schnittstelle finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .

## <a name="requirements"></a>Voraussetzungen

Die Definition dieser Schnittstelle ist als IDL oder C++verfügbar, wie unten gezeigt.

|Definitionstyp|File|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|Atliface. h (auch in "atlbase. h" enthalten)|

##  <a name="createcontrollic"></a>Iaxwinhostwindowlisch:: kreatecontrollic

Erstellt ein lizenziertes Steuerelement, initialisiert es und hostet es im durch `hWnd`identifizierten Fenster.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parameter

*bstrinlisch*<br/>
in Der BSTR-Wert, der den Lizenzschlüssel für das Steuerelement enthält.

### <a name="remarks"></a>Hinweise

Eine Beschreibung der verbleibenden Parameter und des Rückgabewerts finden Sie unter [IAxWinHostWindow:: kreatecontrol](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) .

Das Aufrufen dieser Methode entspricht dem Aufrufen von [iaxwinhostwindowlischen:: createcontrollicex](#createcontrollicex) .

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `IAxWinHostWindowLic::CreateControlLic`finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .

##  <a name="createcontrollicex"></a>Iaxwinhostwindowlisch:: kreatecontrollicex

Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster, ähnlich wie [IAxWinHostWindow:: kreatecontrol](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).

```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parameter

*bstrinlisch*<br/>
in Der BSTR-Wert, der den Lizenzschlüssel für das Steuerelement enthält.

### <a name="remarks"></a>Hinweise

Eine Beschreibung der verbleibenden Parameter und Rückgabewerte finden Sie unter [IAxWinHostWindow:: kreatecontrolex](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) .

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `IAxWinHostWindowLic::CreateControlLicEx`finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .
