---
title: Befehlszuordnungen für DHTML-Bearbeitungsbefehle
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: f4bbfb500e8de9594bbaa334b4e227caeaa845da
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837410"
---
# <a name="dhtml-editing-command-maps"></a>Befehlszuordnungen für DHTML-Bearbeitungsbefehle

Die folgenden Makros können verwendet werden, um DHTML-Bearbeitungsbefehle in [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-abgeleiteten Klassen zuzuordnen. Ein Beispiel für die Verwendung finden Sie unter [HTMLEdit Sample](../../overview/visual-cpp-samples.md).

### <a name="dhtml-editing-command-map-macros"></a>Befehls Zuordnungs Makros für DHTML-Bearbeitungsbefehle

|Name|Beschreibung|
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|Deklariert eine DHTML-Bearbeitungs Befehls Zuordnung in einer Klasse.|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|Startet die Definition einer Befehls Map für die DHTML-Bearbeitungsbefehle in einer Klasse.|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|Markiert das Ende einer Befehls Map für die DHTML-Bearbeitungsbefehle.|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|Ordnet einem HTML-Bearbeitungs Befehl eine Befehls-ID zu.|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|Ordnet einem HTML-Bearbeitungs Befehl und einem Meldungs Handler eine Befehls-ID zu.|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|Ordnet einem HTML-Bearbeitungs Befehl und einem Benutzeroberflächen Element eine Befehls-ID zu.|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|Ordnet einem HTML-Bearbeitungs Befehl, einem Nachrichten Handler und einem Benutzeroberflächen Element eine Befehls-ID zu.|

## <a name="declare_dhtmlediting_cmdmap"></a><a name="declare_dhtmlediting_cmdmap"></a> DECLARE_DHTMLEDITING_CMDMAP

Deklariert eine DHTML-Bearbeitungs Befehls Zuordnung in einer Klasse.

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parameter

*ClassName*<br/>
Der Name der Klasse.

### <a name="remarks"></a>Bemerkungen

Dieses Makro muss in der Definition der von [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)abgeleiteten Klassen verwendet werden.

Verwenden Sie [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap) , um die Zuordnung zu implementieren.

### <a name="example"></a>Beispiel

Siehe [HTMLEdit-Beispiel](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxhtml. h

## <a name="begin_dhtmlediting_cmdmap"></a><a name="begin_dhtmlediting_cmdmap"></a> BEGIN_DHTMLEDITING_CMDMAP

Startet die Definition einer Befehls Map für die DHTML-Bearbeitungsbefehle in einer Klasse.

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parameter

*ClassName*<br/>
Der Name der Klasse, die die Befehls Map für die DHTML-Bearbeitung enthält. Diese Klasse sollte direkt oder indirekt von [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) abgeleitet werden und das [DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap) Makro innerhalb der Klassendefinition einschließen.

### <a name="remarks"></a>Bemerkungen

Fügen Sie Ihrer Klasse eine DHTML-Bearbeitungs Befehls Zuordnung hinzu, um Befehle der Benutzeroberfläche HTML-Bearbeitungs Befehlen zuzuordnen.

Platzieren Sie das BEGIN_DHTMLEDITING_CMDMAP-Makro in der Implementierungs Datei (. cpp) der Klasse, gefolgt von [DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry) Makros für die Befehle, die die Klasse zuordnen soll (z. b. von ID_EDIT_CUT zu IDM_CUT). Verwenden Sie das [END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap) -Makro, um das Ende der Ereignis Zuordnung zu markieren.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxhtml. h

## <a name="end_dhtmlediting_cmdmap"></a><a name="end_dhtmlediting_cmdmap"></a> END_DHTMLEDITING_CMDMAP

Markiert das Ende einer Befehls Map für die DHTML-Bearbeitungsbefehle.

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie in Verbindung mit [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap).

### <a name="example"></a>Beispiel

Siehe [HTMLEdit-Beispiel](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxhtml. h

## <a name="dhtmlediting_cmd_entry"></a><a name="dhtmlediting_cmd_entry"></a> DHTMLEDITING_CMD_ENTRY

Ordnet einem HTML-Bearbeitungs Befehl eine Befehls-ID zu.

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>Parameter

*CMDID*<br/>
Die Befehls-ID (z. b. ID_EDIT_COPY).

*dhtmlcmdid*<br/>
Der HTML-Bearbeitungs Befehl, dem *CMDID zugeordnet wurde* (z. b. IDM_COPY).

### <a name="example"></a>Beispiel

Siehe [HTMLEdit-Beispiel](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxhtml. h

## <a name="dhtmlediting_cmd_entry_func"></a><a name="dhtmlediting_cmd_entry_func"></a> DHTMLEDITING_CMD_ENTRY_FUNC

Ordnet einem HTML-Bearbeitungs Befehl und einem Meldungs Handler eine Befehls-ID zu.

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>Parameter

*CMDID*<br/>
Die Befehls-ID (z. b. ID_EDIT_COPY).

*dhtmlcmdid*<br/>
Der HTML-Bearbeitungs Befehl, dem *CMDID zugeordnet wurde* (z. b. IDM_COPY).

*member_func_name*<br/>
Der Name der nachrichtenhandlerfunktion, der der Befehl zugeordnet ist.

### <a name="example"></a>Beispiel

Siehe [HTMLEdit-Beispiel](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxhtml. h

## <a name="dhtmlediting_cmd_entry_type"></a><a name="dhtmlediting_cmd_entry_type"></a> DHTMLEDITING_CMD_ENTRY_TYPE

Ordnet einem HTML-Bearbeitungs Befehl und einem Benutzeroberflächen Element eine Befehls-ID zu.

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>Parameter

*CMDID*<br/>
Die Befehls-ID (z. b. ID_EDIT_COPY).

*dhtmlcmdid*<br/>
Der HTML-Bearbeitungs Befehl, dem *CMDID zugeordnet wurde* (z. b. IDM_COPY).

*elemtype*<br/>
Der Benutzeroberflächen-Elementtyp. eines der AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX oder AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Beispiel

Siehe [HTMLEdit-Beispiel](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxhtml. h

## <a name="dhtmlediting_cmd_entry_func_type"></a><a name="dhtmlediting_cmd_entry_func_type"></a> DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

Ordnet einem HTML-Bearbeitungs Befehl, einem Nachrichten Handler und einem Benutzeroberflächen Element eine Befehls-ID zu.

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>Parameter

*CMDID*<br/>
Die Befehls-ID (z. b. ID_EDIT_COPY).

*dhtmlcmdid*<br/>
Der HTML-Bearbeitungs Befehl, dem *CMDID zugeordnet wurde* (z. b. IDM_COPY).

*member_func_name*<br/>
Der Name der nachrichtenhandlerfunktion, der der Befehl zugeordnet ist.

*elemtype*<br/>
Der Benutzeroberflächen-Elementtyp. eines der AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX oder AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Beispiel

Siehe [HTMLEdit-Beispiel](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxhtml. h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
