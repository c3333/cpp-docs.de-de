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
ms.openlocfilehash: 6eb6b9e385e9dbc96eb3b62ffb80909e54569e97
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369605"
---
# <a name="cwinformsview-class"></a>CWinFormsView-Klasse

Stellt generische Funktionen zum Hosten eines Windows Forms-Steuerelements als MFC-Ansicht bereit.

## <a name="syntax"></a>Syntax

```
class CWinFormsView : public CView;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinFormsView::CWinFormsView](#cwinformsview)|Erstellt ein `CWinFormsView`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinFormsView::GetControl](#getcontrol)|Ruft einen Zeiger auf das Windows Forms-Steuerelement ab.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name||
|----------|-|
|[CWinFormsView::Operator-Steuerung](#operator_control)|Gibt einen Typ als Zeiger auf ein Windows Forms-Steuerelement um.|

## <a name="remarks"></a>Bemerkungen

MFC verwendet `CWinFormsView` die Klasse, um ein .NET Framework Windows Forms-Steuerelement in einer MFC-Ansicht zu hosten. Das Steuerelement ist ein untergeordnetes Element der systemeigenen Ansicht und nimmt den gesamten Clientbereich der MFC-Ansicht ein. Das Ergebnis ähnelt `CFormView` einer Ansicht, sodass Sie den Windows Forms-Designer und die Laufzeit nutzen können, um umfassende formularbasierte Ansichten zu erstellen.

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden einer Windows Form Benutzersteuerung in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

> [!NOTE]
> Die MFC Windows Forms-Integration funktioniert nur in Projekten, die dynamisch mit MFC verknüpft sind (Projekte, in denen AFXDLL definiert ist).

> [!NOTE]
> CWinFormsView unterstützt das MFC-Splitterfenster ( [CSplitterWnd Class](../../mfc/reference/csplitterwnd-class.md)) nicht. Derzeit wird nur das Windows Forms Splitter-Steuerelement unterstützt.

## <a name="requirements"></a>Anforderungen

**Kopf:** afxwinforms.h

## <a name="cwinformsviewcwinformsview"></a><a name="cwinformsview"></a>CWinFormsView::CWinFormsView

Erstellt ein `CWinFormsView`-Objekt.

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>Parameter

*pManagedViewType*<br/>
Ein Zeiger auf den Datentyp des Windows Forms-Benutzersteuerelements.

### <a name="example"></a>Beispiel

Im folgenden Beispiel `CUserView` erbt die `CWinFormsView` Klasse von und `UserControl1` übergibt den Typ des `CWinFormsView` Konstruktors. `UserControl1`ist ein benutzerdefiniertes Steuerelement in ControlLibrary1.dll.

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

## <a name="cwinformsviewgetcontrol"></a><a name="getcontrol"></a>CWinFormsView::GetControl

Ruft einen Zeiger auf das Windows Forms-Steuerelement ab.

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `System.Windows.Forms.Control`-Objekt.

### <a name="remarks"></a>Bemerkungen

Ein Beispiel für die Verwendung von Windows Forms finden Sie unter [Verwenden einer Windows-Formularbenutzersteuerung in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformsviewoperator-control"></a><a name="operator_control"></a>CWinFormsView::Operator-Steuerung

Gibt einen Typ als Zeiger auf ein Windows Forms-Steuerelement um.

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>Bemerkungen

Mit diesem Operator können `CWinFormsView` Sie eine Ansicht an Funktionen übergeben, die <xref:System.Windows.Forms.Control>einen Zeiger auf ein Windows Forms-Steuerelement vom Typ akzeptieren.

### <a name="example"></a>Beispiel

  Siehe [CWinFormsView::GetControl](#getcontrol).

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWinFormsControl-Klasse](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinFormsDialog-Klasse](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CFormView-Klasse](../../mfc/reference/cformview-class.md)
