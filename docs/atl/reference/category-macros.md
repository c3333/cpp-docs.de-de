---
title: Kategoriemakros
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 0db32c9550cd76fbc8e1f6776b8ecf4cceffebd7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833893"
---
# <a name="category-macros"></a>Kategoriemakros

Diese Makros definieren Kategoriezuordnungen.

|Makro|Beschreibung|
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Markiert den Anfang der Kategoriezuordnung.|
|[END_CATEGORY_MAP](#end_category_map)|Markiert das Ende der Kategoriezuordnung.|
|[IMPLEMENTED_CATEGORY](#implemented_category)|Gibt die Kategorien an, die vom COM-Objekt implementiert werden.|
|[REQUIRED_CATEGORY](#required_category)|Gibt die Kategorien an, die vom COM-Objekt für den Container benötigt werden.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Atlcom. h

## <a name="begin_category_map"></a><a name="begin_category_map"></a> BEGIN_CATEGORY_MAP

Markiert den Anfang der Kategoriezuordnung.

```cpp
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
in Der Name der Klasse, die die Kategoriezuordnung enthält.

### <a name="remarks"></a>Bemerkungen

Die Kategoriezuordnung wird verwendet, um anzugeben, welche Komponenten Kategorien von der com-Klasse implementiert werden und welche Kategorien Sie in Ihrem Container benötigt.

Fügen Sie der Karte für jede Kategorie, die von der com-Klasse implementiert wird, einen [IMPLEMENTED_CATEGORY](#implemented_category) Eintrag hinzu. Fügen Sie der Karte einen [REQUIRED_CATEGORY](#required_category) Eintrag für jede Kategorie hinzu, die von der-Klasse für die Implementierung der-Klasse benötigt wird. Markieren Sie das Ende der Zuordnung mit dem [END_CATEGORY_MAP](#end_category_map) -Makro.

Die in der Zuordnung aufgeführten Komponenten Kategorien werden automatisch registriert, wenn das Modul registriert wird, wenn der Klasse ein [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) oder [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)zugeordnet ist.

> [!NOTE]
> ATL verwendet den Standard-Komponenten Kategorien-Manager zum Registrieren von Komponenten Kategorien. Wenn der Manager beim Registrieren des Moduls nicht auf dem System vorhanden ist, ist die Registrierung erfolgreich, aber die Komponenten Kategorien werden nicht für diese Klasse registriert.

Weitere Informationen zu Komponenten Kategorien finden Sie unter [Was sind Komponenten Kategorien und wie funktionieren Sie](/windows/win32/com/component-categories-and-how-they-work) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="end_category_map"></a><a name="end_category_map"></a> END_CATEGORY_MAP

Markiert das Ende der Kategoriezuordnung.

```cpp
END_CATEGORY_MAP()
```

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [BEGIN_CATEGORY_MAP](#begin_category_map).

## <a name="implemented_category"></a><a name="implemented_category"></a> IMPLEMENTED_CATEGORY

Fügen Sie der [Kategoriezuordnung](#begin_category_map) Ihrer Komponente ein IMPLEMENTED_CATEGORY-Makro hinzu, um anzugeben, dass es als Implementierung der durch den *CATID-* Parameter identifizierten Kategorie registriert werden soll.

```cpp
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>Parameter

*CATID*<br/>
in Eine CATID-Konstante oder Variable, die die Globally Unique Identifier (GUID) für die implementierte Kategorie enthält. Die Adresse von *CATID* wird übernommen und der Zuordnung hinzugefügt. In der folgenden Tabelle finden Sie eine Auswahl von Aktien Kategorien.

### <a name="remarks"></a>Bemerkungen

Die in der Zuordnung aufgeführten Komponenten Kategorien werden automatisch registriert, wenn das Modul registriert ist, wenn die Klasse über eine zugeordnete [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) oder [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) Makro verfügt.

Clients können die für die-Klasse registrierten Kategorieinformationen verwenden, um ihre Funktionen und Anforderungen zu ermitteln, ohne eine Instanz davon erstellen zu müssen.

Weitere Informationen zu Komponenten Kategorien finden Sie unter [Was sind Komponenten Kategorien und wie funktionieren Sie](/windows/win32/com/component-categories-and-how-they-work) in der Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Eine Auswahl von Aktien Kategorien

|Beschreibung|Symbol|Registrierungs-GUID|
|-----------------|------------|-------------------|
|Sicher für Skripterstellung|CATID_SafeForScripting|{7dd95801-9882-11CF-9fa9-00aa006c42c4}|
|Sicher für Initialisierung|CATID_SafeForInitializing|{7dd95802-9882-11CF-9fa9-00aa006c42c4}|
|Kapselung der einfachen Frame Site|CATID_SimpleFrameControl|{157083e0-2368-11CF-87b9-00aa006c8166}|
|einfache Datenbindung|CATID_PropertyNotifyControl|{157083e1-2368-11CF-87b9-00aa006c8166}|
|Erweiterte Datenbindung|CATID_VBDataBound|{157083e2-2368-11CF-87b9-00aa006c8166}|
|Fensterlose Steuerelemente|CATID_WindowlessObject|{1d06b600-3ae3-11CF-87b9-00aa006c8166}|
|Internet fähige Objekte|Eine Beispielliste finden Sie unter [Internet fähige Objekte](/windows/win32/com/internet-aware-objects) in der Windows SDK.||

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="required_category"></a><a name="required_category"></a> REQUIRED_CATEGORY

Fügen Sie der [Kategoriezuordnung](#begin_category_map) Ihrer Komponente ein REQUIRED_CATEGORY-Makro hinzu, um anzugeben, dass es registriert werden soll, wenn die vom *CATID-* Parameter identifizierte Kategorie erforderlich ist.

```cpp
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>Parameter

*CATID*<br/>
in Eine CATID-Konstante oder Variable, die die Globally Unique Identifier (GUID) für die erforderliche Kategorie enthält. Die Adresse von *CATID* wird übernommen und der Zuordnung hinzugefügt. In der folgenden Tabelle finden Sie eine Auswahl von Aktien Kategorien.

### <a name="remarks"></a>Bemerkungen

Die in der Zuordnung aufgeführten Komponenten Kategorien werden automatisch registriert, wenn das Modul registriert ist, wenn die Klasse über eine zugeordnete [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) oder [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) Makro verfügt.

Clients können die für die-Klasse registrierten Kategorieinformationen verwenden, um ihre Funktionen und Anforderungen zu ermitteln, ohne eine Instanz davon erstellen zu müssen. Ein Steuerelement kann beispielsweise erfordern, dass ein Container die Datenbindung unterstützt. Der Container kann ermitteln, ob er über die zum Hosten des Steuer Elements erforderlichen Funktionen verfügt, indem er den kategoriemanager nach den für dieses Steuerelement erforderlichen Kategorien abfragt. Wenn der Container eine erforderliche Funktion nicht unterstützt, kann er das Hosten des COM-Objekts ablehnen.

Weitere Informationen zu Komponenten Kategorien, einschließlich einer Beispielliste, finden [Sie unter Was sind Komponenten Kategorien und wie funktionieren Sie](/windows/win32/com/component-categories-and-how-they-work) in der Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Eine Auswahl von Aktien Kategorien

|Beschreibung|Symbol|Registrierungs-GUID|
|-----------------|------------|-------------------|
|Sicher für Skripterstellung|CATID_SafeForScripting|{7dd95801-9882-11CF-9fa9-00aa006c42c4}|
|Sicher für Initialisierung|CATID_SafeForInitializing|{7dd95802-9882-11CF-9fa9-00aa006c42c4}|
|Kapselung der einfachen Frame Site|CATID_SimpleFrameControl|{157083e0-2368-11CF-87b9-00aa006c8166}|
|einfache Datenbindung|CATID_PropertyNotifyControl|{157083e1-2368-11CF-87b9-00aa006c8166}|
|Erweiterte Datenbindung|CATID_VBDataBound|{157083e2-2368-11CF-87b9-00aa006c8166}|
|Fensterlose Steuerelemente|CATID_WindowlessObject|{1d06b600-3ae3-11CF-87b9-00aa006c8166}|
|Internet fähige Objekte|Eine Beispielliste finden Sie unter [Internet fähige Objekte](/windows/win32/com/internet-aware-objects) in der Windows SDK.||

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>Weitere Informationen

[Makros](../../atl/reference/atl-macros.md)
