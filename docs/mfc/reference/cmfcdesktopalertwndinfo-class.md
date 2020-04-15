---
title: CMFCDesktopAlertWndInfo-Klasse
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_hIcon
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_nURLCmdID
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strText
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strURL
helpviewer_keywords:
- CMFCDesktopAlertWndInfo [MFC], m_hIcon
- CMFCDesktopAlertWndInfo [MFC], m_nURLCmdID
- CMFCDesktopAlertWndInfo [MFC], m_strText
- CMFCDesktopAlertWndInfo [MFC], m_strURL
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
ms.openlocfilehash: f51c1b75e0c096a34b190e36e097aaca4109b5f8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367585"
---
# <a name="cmfcdesktopalertwndinfo-class"></a>CMFCDesktopAlertWndInfo-Klasse

Die `CMFCDesktopAlertWndInfo` Klasse wird mit der [CMFCDesktopAlertWnd-Klasse](../../mfc/reference/cmfcdesktopalertwnd-class.md)verwendet. Bestimmt die Steuerelemente, die angezeigt werden, wenn das Desktopwarnungsfenster angezeigt wird.

## <a name="syntax"></a>Syntax

```
class CMFCDesktopAlertWndInfo
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo::operator=](#operator_eq)||

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)|Ein Handle für das angezeigte Symbol.|
|[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)|Die Befehls-ID, die einem Link im Desktop-Warnungsfenster zugeordnet ist.|
|[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)|Der Text, der im Desktop-Warnfenster angezeigt wird.|
|[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)|Der Link, der im Desktop-Warnungsfenster angezeigt wird.|

## <a name="remarks"></a>Bemerkungen

Die `CMFCDesktopAlertWndInfo` Klasse wird an die [CMFCDesktopAlertWnd::Create-Methode](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) übergeben, um die Elemente anzugeben, die im Standarddialogfeld des Desktopwarnungsfensters angezeigt werden. Das Standarddialogfeld kann drei Elemente enthalten:

- Ein Symbol, das durch Aufrufen von [CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)festgelegt wird.

- Eine Bezeichnung oder Textnachricht, die durch Aufrufen von [CMFCDesktopAlertWndInfo::m_strText](#m_strtext)festgelegt wird.

- Ein Link, der durch Aufrufen von [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)festgelegt wird. Um den Befehl festzulegen, der ausgeführt wird, wenn auf den Link geklickt wird, rufen Sie [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)auf.

Wenn das Standarddialogfeld nicht ausreicht, können Sie ein benutzerdefiniertes Dialogfeld erstellen und es an die [CMFCDesktopAlertWnd::Create-Methode](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) übergeben, anstatt diese Klasse zu verwenden. Weitere Informationen finden Sie unter [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCDesktopAlertWndInfo` wie verschiedene Member in der Klasse verwendet werden. Im Beispiel wird veranschaulicht, wie das Handle auf das angezeigte Symbol, den im Desktop-Warnfenster angezeigten Text, den link, der im Desktopwarnungsfenster angezeigt wird, und die Befehls-ID, die einem Link im Desktop-Warnungsfenster zugeordnet ist, festgelegt wird. Dieses Beispiel ist Teil des [Desktop alert Demo-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxDesktopAlertDialog.h

## <a name="cmfcdesktopalertwndinfooperator"></a><a name="operator_eq"></a>CMFCDesktopAlertWndInfo::operator=

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```

### <a name="parameters"></a>Parameter

[in] *src*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdesktopalertwndinfom_hicon"></a><a name="m_hicon"></a>CMFCDesktopAlertWndInfo::m_hIcon

Ein Handle für das angezeigte Symbol.

```
HICON m_hIcon;
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdesktopalertwndinfom_nurlcmdid"></a><a name="m_nurlcmdid"></a>CMFCDesktopAlertWndInfo::m_nURLCmdID

Die Befehls-ID, die einem Link im Desktop-Warnungsfenster zugeordnet ist.

```
UINT m_nURLCmdID;
```

### <a name="remarks"></a>Bemerkungen

Die Befehls-ID wird an den Besitzer des Popupfensters gesendet, wenn der Benutzer auf den von [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)angegebenen Link klickt.

## <a name="cmfcdesktopalertwndinfom_strtext"></a><a name="m_strtext"></a>CMFCDesktopAlertWndInfo::m_strText

Der Text, der im Desktop-Warnfenster angezeigt wird.

```
CString m_strText;
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdesktopalertwndinfom_strurl"></a><a name="m_strurl"></a>CMFCDesktopAlertWndInfo::m_strURL

Der Link, der im Desktop-Warnungsfenster angezeigt wird.

```
CString m_strURL;
```

### <a name="remarks"></a>Bemerkungen

Wenn der Benutzer auf den Link klickt, wird der Befehl mit der Befehls-ID [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid) an den Besitzer des Popupfensters gesendet.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWnd::Erstellen](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)<br/>
[CMFCDesktopAlertDialog-Klasse](../../mfc/reference/cmfcdesktopalertdialog-class.md)
