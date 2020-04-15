---
title: Befehlszuordnungen für DHTML-Bearbeitungsbefehle
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: 62b388eb178be018655ea2b2be00d7321da50335
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365824"
---
# <a name="dhtml-editing-command-maps"></a>Befehlszuordnungen für DHTML-Bearbeitungsbefehle

Die folgenden Makros können verwendet werden, um DHTML-Bearbeitungsbefehle in [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-derived-Klassen zuzuordnen. Ein Beispiel für ihre Verwendung finden Sie unter [HTMLEdit-Beispiel](../../overview/visual-cpp-samples.md).

### <a name="dhtml-editing-command-map-macros"></a>DHTML-Bearbeitungsbefehl Map-Makros

|||
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|Deklariert eine DHTML-Bearbeitungsbefehlszuordnung in einer Klasse.|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|Startet die Definition einer DHTML-Bearbeitungsbefehlszuordnung innerhalb einer Klasse.|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|Markiert das Ende einer DHTML-Bearbeitungsbefehlszuordnung.|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|Ordnet eine Befehls-ID einem HTML-Bearbeitungsbefehl zu.|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|Ordnet eine Befehls-ID einem HTML-Bearbeitungsbefehl und einem Nachrichtenhandler zu.|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|Ordnet eine Befehls-ID einem HTML-Bearbeitungsbefehl und einem Benutzeroberflächenelement zu.|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|Ordnet eine Befehls-ID einem HTML-Bearbeitungsbefehl, einem Nachrichtenhandler und einem Benutzeroberflächenelement zu.|

## <a name="declare_dhtmlediting_cmdmap"></a><a name="declare_dhtmlediting_cmdmap"></a>DECLARE_DHTMLEDITING_CMDMAP

Deklariert eine DHTML-Bearbeitungsbefehlszuordnung in einer Klasse.

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parameter

*Classname*<br/>
Der Name der Klasse.

### <a name="remarks"></a>Bemerkungen

Dieses Makro wird in der Definition von [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-derived-Klassen verwendet.

Verwenden Sie [BEGIN_DHTMLEDITING_CMDMAP,](#begin_dhtmlediting_cmdmap) um die Karte zu implementieren.

### <a name="example"></a>Beispiel

Siehe [HTMLEdit-Beispiel](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxhtml.h

## <a name="begin_dhtmlediting_cmdmap"></a><a name="begin_dhtmlediting_cmdmap"></a>BEGIN_DHTMLEDITING_CMDMAP

Startet die Definition einer DHTML-Bearbeitungsbefehlszuordnung innerhalb einer Klasse.

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parameter

*Classname*<br/>
Der Name der Klasse, die die DHTML-Bearbeitungsbefehlszuordnung enthält. Diese Klasse sollte direkt oder indirekt von [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) ableiten und das [DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap) Makros in ihre Klassendefinition einbeziehen.

### <a name="remarks"></a>Bemerkungen

Fügen Sie Ihrer Klasse eine DHTML-Bearbeitungsbefehlszuordnung hinzu, um Befehle der Benutzeroberfläche HTML-Bearbeitungsbefehlen zuzuordnen.

Platzieren Sie das BEGIN_DHTMLEDITING_CMDMAP-Makro in der Implementierungsdatei (.cpp) der Klasse, gefolgt von [DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry) Makros für die Befehle, die die Klasse zuordnen soll (z. B. von ID_EDIT_CUT bis IDM_CUT). Verwenden [END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap) Sie das END_DHTMLEDITING_CMDMAP-Makro, um das Ende der Ereigniszuordnung zu markieren.

### <a name="requirements"></a>Anforderungen

  **Header** afxhtml.h

## <a name="end_dhtmlediting_cmdmap"></a><a name="end_dhtmlediting_cmdmap"></a>END_DHTMLEDITING_CMDMAP

Markiert das Ende einer DHTML-Bearbeitungsbefehlszuordnung.

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>Bemerkungen

Verwendung in Verbindung mit [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap).

### <a name="example"></a>Beispiel

Siehe [HTMLEdit-Beispiel](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxhtml.h

## <a name="dhtmlediting_cmd_entry"></a><a name="dhtmlediting_cmd_entry"></a>DHTMLEDITING_CMD_ENTRY

Ordnet eine Befehls-ID einem HTML-Bearbeitungsbefehl zu.

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>Parameter

*cmdID*<br/>
Die Befehls-ID (z. B. ID_EDIT_COPY).

*dhtmlcmdID*<br/>
Der HTML-Bearbeitungsbefehl, dem *cmdID* zugeordnet ist (z. B. IDM_COPY).

### <a name="example"></a>Beispiel

Siehe [HTMLEdit-Beispiel](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxhtml.h

## <a name="dhtmlediting_cmd_entry_func"></a><a name="dhtmlediting_cmd_entry_func"></a>DHTMLEDITING_CMD_ENTRY_FUNC

Ordnet eine Befehls-ID einem HTML-Bearbeitungsbefehl und einem Nachrichtenhandler zu.

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>Parameter

*cmdID*<br/>
Die Befehls-ID (z. B. ID_EDIT_COPY).

*dhtmlcmdID*<br/>
Der HTML-Bearbeitungsbefehl, dem *cmdID* zugeordnet ist (z. B. IDM_COPY).

*member_func_name*<br/>
Der Name der Message-Handler-Funktion, der der Befehl zugeordnet ist.

### <a name="example"></a>Beispiel

Siehe [HTMLEdit-Beispiel](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxhtml.h

## <a name="dhtmlediting_cmd_entry_type"></a><a name="dhtmlediting_cmd_entry_type"></a>DHTMLEDITING_CMD_ENTRY_TYPE

Ordnet eine Befehls-ID einem HTML-Bearbeitungsbefehl und einem Benutzeroberflächenelement zu.

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>Parameter

*cmdID*<br/>
Die Befehls-ID (z. B. ID_EDIT_COPY).

*dhtmlcmdID*<br/>
Der HTML-Bearbeitungsbefehl, dem *cmdID* zugeordnet ist (z. B. IDM_COPY).

*elemType*<br/>
Der Elementtyp der Benutzeroberfläche; AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX oder AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Beispiel

Siehe [HTMLEdit-Beispiel](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxhtml.h

## <a name="dhtmlediting_cmd_entry_func_type"></a><a name="dhtmlediting_cmd_entry_func_type"></a>DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

Ordnet eine Befehls-ID einem HTML-Bearbeitungsbefehl, einem Nachrichtenhandler und einem Benutzeroberflächenelement zu.

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>Parameter

*cmdID*<br/>
Die Befehls-ID (z. B. ID_EDIT_COPY).

*dhtmlcmdID*<br/>
Der HTML-Bearbeitungsbefehl, dem *cmdID* zugeordnet ist (z. B. IDM_COPY).

*member_func_name*<br/>
Der Name der Message-Handler-Funktion, der der Befehl zugeordnet ist.

*elemType*<br/>
Der Elementtyp der Benutzeroberfläche; AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX oder AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Beispiel

Siehe [HTMLEdit-Beispiel](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxhtml.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
