---
title: IAxWinHostWindowlic-Schnittstelle
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
ms.openlocfilehash: 561a65702f1d4f57b4db1afc75769ce4cc523c1c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329914"
---
# <a name="iaxwinhostwindowlic-interface"></a>IAxWinHostWindowlic-Schnittstelle

Diese Schnittstelle stellt Methoden zum Bearbeiten eines lizenzierten Steuerelements und seines Hostobjekts bereit.

## <a name="syntax"></a>Syntax

```
interface IAxWinHostWindowLic : IAxWinHostWindow
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[CreateControlLic](#createcontrollic)|Erstellt ein lizenziertes Steuerelement und fügt es an das Hostobjekt an.|
|[CreateControlLicEx](#createcontrollicex)|Erstellt ein lizenziertes Steuerelement, fügt es an das Hostobjekt an und richtet optional einen Ereignishandler ein.|

## <a name="remarks"></a>Bemerkungen

`IAxWinHostWindowLic`erbt von [IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) und fügt Methoden hinzu, die die Erstellung lizenzierter Steuerelemente unterstützen.

Weitere Informationen finden Sie unter [Hostieren von ActiveX-Steuerelementen mithilfe von ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) für ein Beispiel, das die Member dieser Schnittstelle verwendet.

## <a name="requirements"></a>Anforderungen

Die Definition dieser Schnittstelle ist als IDL oder C++ verfügbar, wie unten gezeigt.

|Definitionstyp|Datei|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (auch in ATLBase.h enthalten)|

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a>IAxWinHostWindowlic::CreateControllic

Erstellt ein lizenziertes Steuerelement, initialisiert es und hostet es in dem Fenster, das von `hWnd`identifiziert wird.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parameter

*bstrLic*<br/>
[in] Der BSTR, der den Lizenzschlüssel für das Steuerelement enthält.

### <a name="remarks"></a>Bemerkungen

Eine Beschreibung der verbleibenden Parameter und des Rückgabewerts finden Sie unter [IAxWinHostWindow::CreateControl.](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)

Das Aufrufen dieser Methode entspricht dem Aufrufen von [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [Hostieren von ActiveX-Steuerelementen unter Verwendung von ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) für ein Beispiel, das `IAxWinHostWindowLic::CreateControlLic`verwendet.

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a>IAxWinHostWindowlic::CreateControllicex

Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster, ähnlich wie [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).

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

*bstrLic*<br/>
[in] Der BSTR, der den Lizenzschlüssel für das Steuerelement enthält.

### <a name="remarks"></a>Bemerkungen

Eine Beschreibung der verbleibenden Parameter und des Rückgabewerts finden Sie unter [IAxWinHostWindow::CreateControlEx.](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex)

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [Hostieren von ActiveX-Steuerelementen unter Verwendung von ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) für ein Beispiel, das `IAxWinHostWindowLic::CreateControlLicEx`verwendet.
