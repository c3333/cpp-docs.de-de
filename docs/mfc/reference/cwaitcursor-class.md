---
title: Cwaitcursor-Klasse
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
ms.openlocfilehash: dfeedad18b3ebcefedff446699f074c86037a4a3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222874"
---
# <a name="cwaitcursor-class"></a>Cwaitcursor-Klasse

Ermöglicht mit einer Befehlszeile die Anzeige eines Wartecursors (normalerweise in Form einer Sanduhr), während ein längeren Vorgang ausgeführt wird.

## <a name="syntax"></a>Syntax

```
class CWaitCursor
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[Cwaitcursor:: cwaitcursor](#cwaitcursor)|Erstellt ein `CWaitCursor` -Objekt und zeigt den warte Cursor an.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Cwaitcursor:: Restore](#restore)|Stellt den warte Cursor wieder her, nachdem er geändert wurde.|

## <a name="remarks"></a>Bemerkungen

`CWaitCursor`weist keine Basisklasse auf.

Gute Windows-Programmierverfahren erfordern, dass Sie immer dann einen Warte Cursor anzeigen, wenn Sie einen Vorgang ausführen, der eine spürbare Zeit in Anspruch nimmt.

Um einen Warte Cursor anzuzeigen, definieren Sie einfach eine `CWaitCursor` Variable vor dem Code, der den langwierigen Vorgang ausführt. Der Konstruktor des Objekts bewirkt, dass der Warte Cursor automatisch angezeigt wird.

Wenn das Objekt den Gültigkeitsbereich verlässt (am Ende des Blocks, in dem das `CWaitCursor` Objekt deklariert ist), legt der Dekonstruktor den Cursor auf den vorherigen Cursor fest. Mit anderen Worten, das-Objekt führt das erforderliche Cleanup automatisch aus.

> [!NOTE]
> Aufgrund der Funktionsweise von Konstruktoren und Debuggern `CWaitCursor` werden Objekte immer als lokale Variablen deklariert – Sie werden nie als globale Variablen deklariert, oder Sie sind nicht mit zugeordnet **`new`** .

Wenn Sie einen Vorgang ausführen, der möglicherweise dazu führt, dass der Cursor geändert wird, z. b. ein Meldungs Feld oder ein Dialogfeld angezeigt wird, rufen Sie die Funktion zum [Wiederherstellen](#restore) des warte Zeigers auf. Es ist auch möglich, `Restore` auch dann aufzurufen, wenn gerade ein warte Cursor angezeigt wird.

Eine andere Möglichkeit zum Anzeigen eines warte Cursors besteht darin, die Kombination aus [CCmdTarget:: beginwaitcursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget:: endwaitcursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)und vielleicht [CCmdTarget:: restorewaitcursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)zu verwenden. Ist jedoch `CWaitCursor` einfacher zu verwenden, da Sie den Cursor nicht auf den vorherigen Cursor festlegen müssen, wenn Sie mit dem langwierigen Vorgang fertig sind.

> [!NOTE]
> Der Cursor wird von MFC mithilfe der virtuellen Funktion [CWinApp::D owaitcursor](../../mfc/reference/cwinapp-class.md#dowaitcursor) festgelegt und wieder hergestellt. Sie können diese Funktion überschreiben, um benutzerdefiniertes Verhalten bereitzustellen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CWaitCursor`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

## <a name="cwaitcursorcwaitcursor"></a><a name="cwaitcursor"></a>Cwaitcursor:: cwaitcursor

Um einen Warte Cursor anzuzeigen, deklarieren Sie einfach ein- `CWaitCursor` Objekt vor dem Code, der den langwierigen Vorgang ausführt.

```
CWaitCursor();
```

### <a name="remarks"></a>Bemerkungen

Der Konstruktor bewirkt, dass der Warte Cursor automatisch angezeigt wird.

Wenn das Objekt den Gültigkeitsbereich verlässt (am Ende des Blocks, in dem das `CWaitCursor` Objekt deklariert ist), legt der Dekonstruktor den Cursor auf den vorherigen Cursor fest. Mit anderen Worten, das-Objekt führt das erforderliche Cleanup automatisch aus.

Sie können die Tatsache nutzen, dass der Dekonstruktor am Ende des Blocks aufgerufen wird (der sich möglicherweise vor dem Ende der Funktion befindet), damit der Warte Cursor nur in einem Teil der Funktion aktiv ist. Dieses Verfahren wird im zweiten Beispiel unten gezeigt.

> [!NOTE]
> Aufgrund der Funktionsweise von Konstruktoren und Debuggern `CWaitCursor` werden Objekte immer als lokale Variablen deklariert – Sie werden nie als globale Variablen deklariert, und Sie sind nicht mit zugeordnet **`new`** .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

## <a name="cwaitcursorrestore"></a><a name="restore"></a>Cwaitcursor:: Restore

Um den warte Cursor wiederherzustellen, müssen Sie diese Funktion nach dem Ausführen eines Vorgangs (z. b. Anzeigen eines Meldungs Felds oder Dialog Felds) abrufen, das möglicherweise den warte Cursor auf einen anderen Cursor ändert.

```cpp
void Restore();
```

### <a name="remarks"></a>Bemerkungen

Es ist in Ordnung, `Restore` auch dann aufzurufen, wenn der Warte Cursor aktuell angezeigt wird.

Wenn Sie den warte Cursor in einer anderen Funktion als der, in der das `CWaitCursor` Objekt deklariert ist, wiederherstellen müssen, können Sie [CCmdTarget:: restorewaitcursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)verwenden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>Siehe auch

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget:: beginwaitcursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget:: endwaitcursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget:: restorewaitcursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp::D owaitcursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[Gewusst wie: Ändern des Mauszeigers in einer Microsoft Foundation Class-Anwendung](https://go.microsoft.com/fwlink/p/?linkid=128044)
