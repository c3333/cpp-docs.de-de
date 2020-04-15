---
title: CJumpList-Klasse
ms.date: 03/27/2019
f1_keywords:
- CJumpList
- AFXADV/CJumpList
- AFXADV/CJumpList::CJumpList
- AFXADV/CJumpList::AbortList
- AFXADV/CJumpList::AddDestination
- AFXADV/CJumpList::AddKnownCategory
- AFXADV/CJumpList::AddTask
- AFXADV/CJumpList::AddTasks
- AFXADV/CJumpList::AddTaskSeparator
- AFXADV/CJumpList::ClearAll
- AFXADV/CJumpList::ClearAllDestinations
- AFXADV/CJumpList::CommitList
- AFXADV/CJumpList::GetDestinationList
- AFXADV/CJumpList::GetMaxSlots
- AFXADV/CJumpList::GetRemovedItems
- AFXADV/CJumpList::InitializeList
- AFXADV/CJumpList::SetAppID
helpviewer_keywords:
- CJumpList [MFC], CJumpList
- CJumpList [MFC], AbortList
- CJumpList [MFC], AddDestination
- CJumpList [MFC], AddKnownCategory
- CJumpList [MFC], AddTask
- CJumpList [MFC], AddTasks
- CJumpList [MFC], AddTaskSeparator
- CJumpList [MFC], ClearAll
- CJumpList [MFC], ClearAllDestinations
- CJumpList [MFC], CommitList
- CJumpList [MFC], GetDestinationList
- CJumpList [MFC], GetMaxSlots
- CJumpList [MFC], GetRemovedItems
- CJumpList [MFC], InitializeList
- CJumpList [MFC], SetAppID
ms.assetid: d364d27e-f512-4b12-9872-c2a17c78ab1f
ms.openlocfilehash: 98d6bec3d33c9060ebb741111dff793f64cc7cb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372335"
---
# <a name="cjumplist-class"></a>CJumpList-Klasse

A `CJumpList` ist die Liste der Verknüpfungen, die angezeigt werden, wenn Sie mit der rechten Maustaste auf ein Symbol in der Taskleiste klicken.

## <a name="syntax"></a>Syntax

```
class CJumpList;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CJumpList::CJumpList](#cjumplist)|Erstellt ein `CJumpList`-Objekt.|
|[CJumpList::'CJumpList](#_dtorcjumplist)|Zerstört ein `CJumpList` -Objekt.|

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CJumpList::AbortList](#abortlist)|Bricht eine Listerstellungstransaktion ab, ohne eine Bindung zu übernehmen.|
|[CJumpList::AddDestination](#adddestination)|Ist überladen. Fügt der Liste das Ziel hinzu.|
|[CJumpList::AddKnownCategory](#addknowncategory)|Fügt eine bekannte Kategorie an die Liste an.|
|[CJumpList::AddTask](#addtask)|Ist überladen. Fügt elemente zur Kategorie kanonische Aufgaben hinzu.|
|[CJumpList::AddTasks](#addtasks)|Fügt elemente zur Kategorie kanonische Aufgaben hinzu.|
|[CJumpList::AddTaskSeparator](#addtaskseparator)|Fügt ein Trennzeichen zwischen Vorgängen hinzu.|
|[CJumpList::ClearAll](#clearall)|Entfernt alle Aufgaben und Ziele, die der `CJumpList` aktuellen Instanz bisher hinzugefügt wurden.|
|[CJumpList::ClearAllDestinations](#clearalldestinations)|Entfernt alle Ziele, die der aktuellen `CJumpList` Instanz bisher hinzugefügt wurden.|
|[CJumpList::CommitList](#commitlist)|Beendet eine Listenerstellungstransaktion und überträgt die gemeldete Liste an den zugeordneten Speicher (in diesem Fall die Registrierung).|
|[CJumpList::GetDestinationList](#getdestinationlist)|Ruft einen Schnittstellenzeiger zur Zielliste ab.|
|[CJumpList::GetMaxSlots](#getmaxslots)|Ruft die maximale Anzahl von Elementen ab, einschließlich Kategorieüberschriften, die im Zielmenü der aufrufenden Anwendung angezeigt werden können.|
|[CJumpList::GetRemovedItems](#getremoveditems)|Gibt ein Array von Elementen zurück, die entfernte Ziele darstellen.|
|[CJumpList::InitializeList](#initializelist)|Startet eine Listenerstellungstransaktion.|
|[CJumpList::SetAppID](#setappid)|Legt die Anwendungsbenutzermodell-ID für die Liste fest, die erstellt wird.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CJumpList](../../mfc/reference/cjumplist-class.md)

## <a name="requirements"></a>Anforderungen

**Kopf:** afxadv.h

## <a name="cjumplistcjumplist"></a><a name="_dtorcjumplist"></a>CJumpList::'CJumpList

Zerstört ein `CJumpList` -Objekt.

```
~CJumpList();
```

## <a name="cjumplistabortlist"></a><a name="abortlist"></a>CJumpList::AbortList

Bricht eine Listerstellungstransaktion ab, ohne eine Bindung zu übernehmen.

```
void AbortList();
```

### <a name="remarks"></a>Bemerkungen

Das Aufrufen dieser Methode hat `CJumpList` den `CommitList`gleichen Effekt wie das Zerstören ohne Aufruf .

## <a name="cjumplistadddestination"></a><a name="adddestination"></a>CJumpList::AddDestination

Fügt der Liste das Ziel hinzu.

```
BOOL AddDestination(
    LPCTSTR lpcszCategoryName,
    LPCTSTR strDestinationPath);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellItem* pShellItem);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellLink* pShellLink);
```

### <a name="parameters"></a>Parameter

*lpcszCategoryName*<br/>
Gibt einen Kategorienamen an. Wenn die angegebene Kategorie nicht vorhanden ist, wird sie erstellt.

*strDestinationPath*<br/>
Gibt einen Pfad zur Zieldatei an.

*strCategoryName*<br/>
Gibt einen Kategorienamen an. Wenn die angegebene Kategorie nicht vorhanden ist, wird sie erstellt.

*pShellItem*<br/>
Gibt ein Shell-Element an, das das hinzugefügte Ziel darstellt.

*pShellLink*<br/>
Gibt eine Shellverknüpfung an, die das hinzugefügte Ziel darstellt.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Die Instanz `CJumpList` von intern sammelt hinzugefügte Ziele `CommitList`und überträgt sie dann in .

## <a name="cjumplistaddknowncategory"></a><a name="addknowncategory"></a>CJumpList::AddKnownCategory

Fügt eine bekannte Kategorie an die Liste an.

```
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```

### <a name="parameters"></a>Parameter

*category*<br/>
Gibt einen bekannten Kategorietyp an. Kann entweder KDC_RECENT oder KDC_KNOWN sein.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Bekannte Kategorien sind die häufigen und letzten Kategorien, die `SHAddToRecentDocs` wir automatisch für jede Anwendung berechnen, die verwendet wird (oder sie indirekt verwendet, wenn die Shell sie im Auftrag der Anwendung in einigen Szenarien aufruft).

## <a name="cjumplistaddtask"></a><a name="addtask"></a>CJumpList::AddTask

Fügt elemente zur Kategorie kanonische Aufgaben hinzu.

```
BOOL AddTask(
    LPCTSTR strTargetExecutablePath,
    LPCTSTR strCommandLineArgs,
    LPCTSTR strTitle,
    LPCTSTR strIconLocation,
    int iIconIndex);

BOOL AddTask(IShellLink* pShellLink);
```

### <a name="parameters"></a>Parameter

*strTargetExecutablePath*<br/>
Gibt den Zielaufgabenpfad an.

*strCommandLineArgs*<br/>
Gibt Befehlszeilenargumente der ausführbaren Datei an, die von *strTargetExecutablePath*angegeben wird.

*strTitle*<br/>
Aufgabenname, der in der Zielliste angezeigt wird.

*strIconLocation*<br/>
Position des Symbols, das zusammen mit dem Titel in der Zielliste angezeigt wird.

*iIconIndex*<br/>
Icon-Index.

*pShellLink*<br/>
Shell-Verknüpfung, die eine hinzuzufügende Aufgabe darstellt.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Die Instanz `CJumpList` der akkumuliert bestimmte Aufgaben und `CommitList`fügt sie der Zielliste während hinzu. Aufgabenelemente werden in einer Kategorie am unteren Rand des Zielmenüs der Anwendung angezeigt. Diese Kategorie hat Vorrang vor allen anderen Kategorien, wenn sie in der Benutzeroberfläche ausgefüllt wird.

## <a name="cjumplistaddtasks"></a><a name="addtasks"></a>CJumpList::AddTasks

Fügt elemente zur Kategorie kanonische Aufgaben hinzu.

```
BOOL AddTasks(IObjectArray* pObjectCollection);
```

### <a name="parameters"></a>Parameter

*pObjectCollection*<br/>
Eine Auflistung von Aufgaben, die hinzugefügt werden sollen.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Die Instanz von CJumpList sammelt bestimmte Aufgaben und `CommitList`fügt sie während der Zielliste hinzu. Aufgabenelemente werden in einer Kategorie am unteren Rand des Zielmenüs der Anwendung angezeigt. Diese Kategorie hat Vorrang vor allen anderen Kategorien, wenn sie in der Benutzeroberfläche ausgefüllt wird.

## <a name="cjumplistaddtaskseparator"></a><a name="addtaskseparator"></a>CJumpList::AddTaskSeparator

Fügt ein Trennzeichen zwischen Vorgängen hinzu.

```
BOOL AddTaskSeparator();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn er erfolgreich ist, 0, wenn dies nicht der Fall ist.

## <a name="cjumplistcjumplist"></a><a name="cjumplist"></a>CJumpList::CJumpList

Erstellt ein `CJumpList`-Objekt.

```
CJumpList(BOOL bAutoCommit = TRUE);
```

### <a name="parameters"></a>Parameter

*bAutoCommit*<br/>
Wenn dieser Parameter FALSE ist, wird die Liste nicht automatisch im Destruktor festgeschrieben.

## <a name="cjumplistclearall"></a><a name="clearall"></a>CJumpList::ClearAll

Entfernt alle Aufgaben und Ziele, die der `CJumpList` aktuellen Instanz bisher hinzugefügt wurden.

```
void ClearAll();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode löscht und gibt alle Daten und internen Schnittstellen frei.

## <a name="cjumplistclearalldestinations"></a><a name="clearalldestinations"></a>CJumpList::ClearAllDestinations

Entfernt alle Ziele, die der aktuellen CJumpList-Instanz bisher hinzugefügt wurden.

```
void ClearAllDestinations();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, wenn Sie alle Ziele entfernen müssen, die bisher in der aktuellen Sitzung der Ziellistenerstellung hinzugefügt wurden, und weitere Ziele erneut hinzufügen müssen. Wenn das `ICustomDestinationList` Innere initialisiert wurde, bleibt es am Leben.

## <a name="cjumplistcommitlist"></a><a name="commitlist"></a>CJumpList::CommitList

Beendet eine Listerstellungstransaktion und überträgt die gemeldete Liste an den zugeordneten Speicher (in diesem Fall die Registrierung).

```
BOOL CommitList();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Der Commit ist atomar. Ein Fehler wird zurückgegeben, wenn der Commit fehlschlägt.  Wenn `CommitList` aufgerufen wird, wird die aktuelle Liste der entfernten Elemente bereinigt. Wenn Sie diese Methode aufrufen, wird das Objekt so zurückgesetzt, dass es keine aktive Listenerstellungstransaktion hat. Um die Liste `BeginList` zu aktualisieren, muss erneut aufgerufen werden.

## <a name="cjumplistgetdestinationlist"></a><a name="getdestinationlist"></a>CJumpList::GetDestinationList

Ruft einen Schnittstellenzeiger zur Zielliste ab.

```
ICustomDestinationList* GetDestinationList();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Wenn die Sprungliste nicht initialisiert oder festgeschrieben oder abgebrochen wurde, ist der zurückgegebene Wert NULL.

## <a name="cjumplistgetmaxslots"></a><a name="getmaxslots"></a>CJumpList::GetMaxSlots

Ruft die maximale Anzahl von Elementen ab, einschließlich Kategorieüberschriften, die im Zielmenü der aufrufenden Anwendung angezeigt werden können.

```
UINT GetMaxSlots() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Anwendungen können nur eine Reihe von Elementen und Kategorieüberschriften melden, die bis zu diesem Wert kombiniert sind. Wenn Aufrufe `AppendCategory` `AppendKnownCategory`von `AddUserTasks` , oder diese Zahl überschreiten, geben sie einen Fehler zurück.

## <a name="cjumplistgetremoveditems"></a><a name="getremoveditems"></a>CJumpList::GetRemovedItems

Gibt ein Array von Elementen zurück, die entfernte Ziele darstellen.

```
IObjectArray* GetRemovedItems();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Die entfernten Ziele werden während der Initialisierung der Sprungliste abgerufen. Beim Generieren einer neuen Zielliste wird erwartet, dass Anwendungen zuerst die Liste der entfernten Ziele verarbeiten und ihre Nachverfolgungsdaten für jedes Element löschen, das vom entfernten Listenzähler zurückgegeben wird. Wenn eine Anwendung versucht, ein Element bereitzustellen, das gerade `BeginList` in der Transaktion entfernt wurde, die der aktuelle Aufruf gestartet hat, schlägt der Methodenaufruf, der dieses Element erneut hinzugefügt hat, fehl, um sicherzustellen, dass Anwendungen die entfernte Liste respektieren.

## <a name="cjumplistinitializelist"></a><a name="initializelist"></a>CJumpList::InitializeList

Startet eine Listenerstellungstransaktion.

```
BOOL InitializeList();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Sie müssen diese Methode nicht explizit aufrufen, es sei `ICustomDestinationList` denn, Sie möchten einen Zeiger auf die Verwendung `GetDestinationList`abrufen, die Anzahl der verfügbaren Steckplätze mit `GetMaxSlots`, oder eine Liste der entfernten Elemente mithilfe `GetRemovedItems`.

## <a name="cjumplistsetappid"></a><a name="setappid"></a>CJumpList::SetAppID

Legt die Anwendungsbenutzermodell-ID für die Liste fest, die erstellt wird.

```
void SetAppID(LPCTSTR strAppID);
```

### <a name="parameters"></a>Parameter

*strAppID*<br/>
Eine Zeichenfolge, die die Anwendungsbenutzermodell-ID angibt.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
