---
title: Kategorie Makros
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 1d8bbae4608aa661bbc612604f7d85855f325f5f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321599"
---
# <a name="category-macros"></a>Kategorie Makros

Diese Makros definieren Kategoriezuordnungen.

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Markiert den Anfang der Kategoriekarte.|
|[END_CATEGORY_MAP](#end_category_map)|Markiert das Ende der Kategoriezuordnung.|
|[IMPLEMENTED_CATEGORY](#implemented_category)|Gibt Kategorien an, die vom COM-Objekt implementiert werden.|
|[REQUIRED_CATEGORY](#required_category)|Gibt Kategorien an, die vom COM-Objekt für den Container erforderlich sind.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="begin_category_map"></a><a name="begin_category_map"></a>BEGIN_CATEGORY_MAP

Markiert den Anfang der Kategoriekarte.

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
[in] Der Name der Klasse, die die Kategoriezuordnung enthält.

### <a name="remarks"></a>Bemerkungen

Die Kategoriezuordnung wird verwendet, um anzugeben, welche Komponentenkategorien die COM-Klasse implementieren soll und welche Kategorien sie aus ihrem Container benötigt.

Fügen Sie der Karte einen [IMPLEMENTED_CATEGORY](#implemented_category) Eintrag für jede Kategorie hinzu, die von der COM-Klasse implementiert wurde. Fügen Sie der Karte einen [REQUIRED_CATEGORY](#required_category) Eintrag für jede Kategorie hinzu, für die die Klasse die Implementierung ihrer Clients benötigt. Markieren Sie das Ende der Karte mit dem [END_CATEGORY_MAP](#end_category_map) Makro.

Die in der Karte aufgeführten Komponentenkategorien werden automatisch registriert, wenn das Modul registriert wird, wenn der Klasse ein [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) oder [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)zugeordnet ist.

> [!NOTE]
> ATL verwendet den Standardkomponentenkategorien-Manager, um Komponentenkategorien zu erfassen. Wenn der Manager bei der Registrierung des Moduls nicht auf dem System vorhanden ist, ist die Registrierung erfolgreich, aber die Komponentenkategorien werden nicht für diese Klasse registriert.

Weitere Informationen zu Komponentenkategorien finden Sie unter [Was sind Komponentenkategorien und wie funktionieren sie](/windows/win32/com/component-categories-and-how-they-work) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="end_category_map"></a><a name="end_category_map"></a>END_CATEGORY_MAP

Markiert das Ende der Kategoriezuordnung.

```
END_CATEGORY_MAP()
```

### <a name="example"></a>Beispiel

Siehe Beispiel für [BEGIN_CATEGORY_MAP](#begin_category_map).

## <a name="implemented_category"></a><a name="implemented_category"></a>IMPLEMENTED_CATEGORY

Fügen Sie der [Kategoriezuordnung](#begin_category_map) Ihrer Komponente ein IMPLEMENTED_CATEGORY-Makro hinzu, um anzugeben, dass es als Implementierung der Kategorie registriert werden soll, die durch den *catID-Parameter* identifiziert wird.

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>Parameter

*Catid*<br/>
[in] Eine CATID-Konstante oder -Variable, die den global eindeutigen Bezeichner (GUID) für die implementierte Kategorie hält. Die Adresse von *catID* wird genommen und der Karte hinzugefügt. Eine Auswahl der Bestandskategorien finden Sie in der nachstehenden Tabelle.

### <a name="remarks"></a>Bemerkungen

Die in der Karte aufgeführten Komponentenkategorien werden automatisch registriert, wenn das Modul registriert wird, wenn der Klasse ein [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) oder [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) Makro zugeordnet ist.

Clients können die für die Klasse registrierten Kategorieinformationen verwenden, um ihre Fähigkeiten und Anforderungen zu bestimmen, ohne eine Instanz davon erstellen zu müssen.

Weitere Informationen zu Komponentenkategorien finden Sie unter [Was sind Komponentenkategorien und wie funktionieren sie](/windows/win32/com/component-categories-and-how-they-work) im Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Eine Auswahl von Aktienkategorien

|BESCHREIBUNG|Symbol|Registrierungs-GUID|
|-----------------|------------|-------------------|
|Sicher für Scripting|CATID_SafeForScripting|7DD95801-9882-11CF-9FA9-00AA006C42C4|
|Sicher für die Initialisierung|CATID_SafeForInitializing|7DD95802-9882-11CF-9FA9-00AA006C42C4|
|Einfaches Frame Site Containment|CATID_SimpleFrameControl|Nr. 157083E0-2368-11cf-87B9-00AA006C8166|
|einfache Datenbindung|CATID_PropertyNotifyControl|Nr. 157083E1-2368-11cf-87B9-00AA006C8166|
|Erweiterte Datenbindung|CATID_VBDataBound|Nr. 157083E2-2368-11cf-87B9-00AA006C8166|
|Fensterlose Steuerelemente|CATID_WindowlessObject|1D06B600-3AE3-11cf-87B9-00AA006C8166|
|Internet-Aware-Objekte|Eine Beispielliste finden Sie unter [InternetAware Objects](/windows/win32/com/internet-aware-objects) in the Windows SDK.||

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="required_category"></a><a name="required_category"></a>REQUIRED_CATEGORY

Fügen Sie der [Kategoriezuordnung](#begin_category_map) Ihrer Komponente ein REQUIRED_CATEGORY-Makro hinzu, um anzugeben, dass es als die Kategorie registriert werden soll, die durch den *catID-Parameter* identifiziert wurde.

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>Parameter

*Catid*<br/>
[in] Eine CATID-Konstante oder -Variable, die den guiD (Globally Unique Identifier) für die erforderliche Kategorie hält. Die Adresse von *catID* wird genommen und der Karte hinzugefügt. Eine Auswahl der Bestandskategorien finden Sie in der nachstehenden Tabelle.

### <a name="remarks"></a>Bemerkungen

Die in der Karte aufgeführten Komponentenkategorien werden automatisch registriert, wenn das Modul registriert wird, wenn der Klasse ein [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) oder [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) Makro zugeordnet ist.

Clients können die für die Klasse registrierten Kategorieinformationen verwenden, um ihre Fähigkeiten und Anforderungen zu bestimmen, ohne eine Instanz davon erstellen zu müssen. Ein Steuerelement kann z. B. erfordern, dass ein Container die Datenbindung unterstützt. Der Container kann herausfinden, ob er über die erforderlichen Funktionen zum Hosten des Steuerelements verfügt, indem er den Kategorie-Manager nach den Kategorien abfragt, die für dieses Steuerelement erforderlich sind. Wenn der Container ein erforderliches Feature nicht unterstützt, kann er das Hosten des COM-Objekts verweigern.

Weitere Informationen zu Komponentenkategorien, einschließlich einer Beispielliste, finden Sie unter [Was sind Komponentenkategorien und wie funktionieren sie](/windows/win32/com/component-categories-and-how-they-work) im Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Eine Auswahl von Aktienkategorien

|BESCHREIBUNG|Symbol|Registrierungs-GUID|
|-----------------|------------|-------------------|
|Sicher für Scripting|CATID_SafeForScripting|7DD95801-9882-11CF-9FA9-00AA006C42C4|
|Sicher für die Initialisierung|CATID_SafeForInitializing|7DD95802-9882-11CF-9FA9-00AA006C42C4|
|Einfaches Frame Site Containment|CATID_SimpleFrameControl|Nr. 157083E0-2368-11cf-87B9-00AA006C8166|
|einfache Datenbindung|CATID_PropertyNotifyControl|Nr. 157083E1-2368-11cf-87B9-00AA006C8166|
|Erweiterte Datenbindung|CATID_VBDataBound|Nr. 157083E2-2368-11cf-87B9-00AA006C8166|
|Fensterlose Steuerelemente|CATID_WindowlessObject|1D06B600-3AE3-11cf-87B9-00AA006C8166|
|Internet-Aware-Objekte|Eine Beispielliste finden Sie unter [InternetAware Objects](/windows/win32/com/internet-aware-objects) in the Windows SDK.||

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)
