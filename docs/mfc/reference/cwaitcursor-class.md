---
title: CWaitCursor-Klasse
ms.date: 11/04/2016
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
ms.openlocfilehash: 48ef8f9c965f54deafcc62451639f8c31021e900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373180"
---
# <a name="cwaitcursor-class"></a>CWaitCursor-Klasse

Ermöglicht mit einer Befehlszeile die Anzeige eines Wartecursors (normalerweise in Form einer Sanduhr), während ein längeren Vorgang ausgeführt wird.

## <a name="syntax"></a>Syntax

```
class CWaitCursor
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWaitCursor::CWaitCursor](#cwaitcursor)|Erstellt ein `CWaitCursor` Objekt und zeigt den Wartecursor an.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWaitCursor::Wiederherstellen](#restore)|Stellt den Wartecursor wieder her, nachdem er geändert wurde.|

## <a name="remarks"></a>Bemerkungen

`CWaitCursor`hat keine Basisklasse.

Gute Windows-Programmiermethoden erfordern, dass Sie einen Wartecursor anzeigen, wenn Sie einen Vorgang ausführen, der eine spürbare Zeit in Anspruch nimmt.

Um einen Wartecursor anzuzeigen, `CWaitCursor` definieren Sie einfach eine Variable vor dem Code, der den langwierigen Vorgang ausführt. Der Konstruktor des Objekts bewirkt automatisch, dass der Wartecursor angezeigt wird.

Wenn das Objekt den Gültigkeitsbereich verlässt (am `CWaitCursor` Ende des Blocks, in dem das Objekt deklariert wird), setzt sein Destruktor den Cursor auf den vorherigen Cursor. Mit anderen Worten, das Objekt führt die erforderliche Bereinigung automatisch durch.

> [!NOTE]
> Aufgrund der Funktionsweise ihrer Konstruktoren und `CWaitCursor` Destruktoren werden Objekte immer als lokale Variablen deklariert – sie werden nie als globale Variablen deklariert, noch werden sie mit **neuen**zugewiesen.

Wenn Sie einen Vorgang ausführen, der dazu führen kann, dass der Cursor geändert wird, z. B. ein Meldungs- oder Dialogfeld, rufen Sie die Memberfunktion [Wiederherstellen](#restore) auf, um den Wartecursor wiederherzustellen. Es ist in `Restore` Ordnung, auch dann aufzurufen, wenn derzeit ein Wartecursor angezeigt wird.

Eine andere Möglichkeit, einen Wartecursor anzuzeigen, ist die Kombination von [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)und möglicherweise [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). Es `CWaitCursor` ist jedoch einfacher zu verwenden, da Sie den Cursor nicht auf den vorherigen Cursor setzen müssen, wenn Sie mit dem langwierigen Vorgang fertig sind.

> [!NOTE]
> MFC legt den Cursor mithilfe der virtuellen Funktion [CWinApp::DoWaitCursor fest](../../mfc/reference/cwinapp-class.md#dowaitcursor) und stellt ihn wieder her. Sie können diese Funktion überschreiben, um benutzerdefiniertes Verhalten bereitzustellen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CWaitCursor`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

## <a name="cwaitcursorcwaitcursor"></a><a name="cwaitcursor"></a>CWaitCursor::CWaitCursor

Um einen Wartecursor anzuzeigen, `CWaitCursor` deklarieren Sie einfach ein Objekt vor dem Code, der den langwierigen Vorgang ausführt.

```
CWaitCursor();
```

### <a name="remarks"></a>Bemerkungen

Der Konstruktor bewirkt automatisch, dass der Wartecursor angezeigt wird.

Wenn das Objekt den Gültigkeitsbereich verlässt (am `CWaitCursor` Ende des Blocks, in dem das Objekt deklariert wird), setzt sein Destruktor den Cursor auf den vorherigen Cursor. Mit anderen Worten, das Objekt führt die erforderliche Bereinigung automatisch durch.

Sie können die Tatsache nutzen, dass der Destruktor am Ende des Blocks aufgerufen wird (was möglicherweise vor dem Ende der Funktion liegt), um den Wartecursor nur in einem Teil Ihrer Funktion aktiv zu machen. Diese Technik wird im zweiten Beispiel unten gezeigt.

> [!NOTE]
> Aufgrund der Funktionsweise ihrer Konstruktoren und `CWaitCursor` Destruktoren werden Objekte immer als lokale Variablen deklariert – sie werden nie als globale Variablen deklariert, noch werden sie mit **neuen**zugewiesen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

## <a name="cwaitcursorrestore"></a><a name="restore"></a>CWaitCursor::Wiederherstellen

Um den Wartecursor wiederherzustellen, rufen Sie diese Funktion auf, nachdem Sie einen Vorgang ausgeführt haben, z. B. das Anzeigen eines Meldungs- oder Dialogfelds, wodurch der Wartecursor in einen anderen Cursor geändert werden kann.

```
void Restore();
```

### <a name="remarks"></a>Bemerkungen

Es ist in `Restore` Ordnung, auch dann aufzurufen, wenn der Wartecursor gerade angezeigt wird.

Wenn Sie den Wartecursor wiederherstellen müssen, während Sie sich `CWaitCursor` in einer anderen Funktion als der Funktion befinden, in der das Objekt deklariert ist, können Sie [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)aufrufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[Wie kann ich: Ändern des Mauscursors in einer Microsoft Foundation-Klassenanwendung](https://go.microsoft.com/fwlink/p/?linkid=128044)
