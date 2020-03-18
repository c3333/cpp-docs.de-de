---
title: CWinFormsView-Klasse
ms.date: 11/04/2016
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
ms.openlocfilehash: f4a5e6b88527dad8606092ccebd4899bba5181f6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426288"
---
# <a name="cwinformsview-class"></a>CWinFormsView-Klasse

Stellt generische Funktionen zum Hosten eines Windows Forms-Steuerelements als MFC-Ansicht bereit.

## <a name="syntax"></a>Syntax

```
class CWinFormsView : public CView;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CWinFormsView:: CWinFormsView](#cwinformsview)|Erstellt ein `CWinFormsView`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CWinFormsView:: GetControl](#getcontrol)|Ruft einen Zeiger auf das Windows Forms Steuerelement ab.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name||
|----------|-|
|[CWinFormsView:: Operator-Steuerelement ^](#operator_control)|Wandelt einen Typ als Zeiger in ein Windows Forms Steuerelement um.|

## <a name="remarks"></a>Hinweise

MFC verwendet die `CWinFormsView`-Klasse, um ein .NET Framework Windows Forms-Steuerelement in einer MFC-Ansicht zu hosten. Das-Steuerelement ist ein untergeordnetes Element der nativen Ansicht und belegt den gesamten Client Bereich der MFC-Ansicht. Das Ergebnis ähnelt einer `CFormView` Ansicht, sodass Sie den Windows Forms Designer und die Laufzeit nutzen können, um umfangreiche Formular basierte Sichten zu erstellen.

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden eines Windows Form-Benutzer Steuer Elements in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

> [!NOTE]
>  Die MFC-Windows Forms Integration funktioniert nur in Projekten, die dynamisch mit MFC verknüpft sind (Projekte, in denen AFXDLL definiert ist).

> [!NOTE]
>  CWinFormsView unterstützt das MFC-Splitter Fenster ( [CSplitterWnd-Klasse](../../mfc/reference/csplitterwnd-class.md)) nicht. Derzeit wird nur das Windows Forms Splitter-Steuerelement unterstützt.

## <a name="requirements"></a>Voraussetzungen

**Header:** afxwinforms. h

##  <a name="cwinformsview"></a>CWinFormsView:: CWinFormsView

Erstellt ein `CWinFormsView`-Objekt.

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>Parameter

*pmanagedviewtype*<br/>
Ein Zeiger auf den Datentyp des Windows Forms Benutzer Steuer Elements.

### <a name="example"></a>Beispiel

Im folgenden Beispiel erbt die `CUserView`-Klasse von `CWinFormsView` und übergibt den Typ von `UserControl1` an den `CWinFormsView`-Konstruktor. `UserControl1` ist ein benutzerdefiniertes Steuerelement in ControlLibrary1. dll.

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

##  <a name="getcontrol"></a>CWinFormsView:: GetControl

Ruft einen Zeiger auf das Windows Forms Steuerelement ab.

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `System.Windows.Forms.Control` -Objekt.

### <a name="remarks"></a>Hinweise

Ein Beispiel für die Verwendung von Windows Forms finden Sie unter [Verwenden eines Windows Form-Benutzer Steuer Elements in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="operator_control"></a>CWinFormsView:: Operator-Steuerelement ^

Wandelt einen Typ als Zeiger in ein Windows Forms Steuerelement um.

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>Hinweise

Dieser Operator ermöglicht es Ihnen, eine `CWinFormsView` Ansicht an Funktionen zu übergeben, die einen Zeiger auf ein Windows Forms Steuerelement des Typs <xref:System.Windows.Forms.Control>akzeptieren.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie unter [CWinFormsView:: GetControl](#getcontrol).

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWinFormsControl-Klasse](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinFormsDialog-Klasse](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CFormView-Klasse](../../mfc/reference/cformview-class.md)
