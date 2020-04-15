---
title: CCreateContext-Struktur
ms.date: 11/04/2016
f1_keywords:
- CCreateContext
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
ms.openlocfilehash: 29fc6210b9888b6a5ba5aaf15b66242c29c15dc8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369384"
---
# <a name="ccreatecontext-structure"></a>CCreateContext-Struktur

Das Framework `CCreateContext` verwendet die Struktur, wenn es die Rahmenfenster und Ansichten erstellt, die einem Dokument zugeordnet sind.

## <a name="syntax"></a>Syntax

```
struct CCreateContext
```

## <a name="remarks"></a>Bemerkungen

`CCreateContext`ist eine Struktur und hat keine Basisklasse.

Wenn Sie ein Fenster erstellen, stellen die Werte in dieser Struktur die Informationen bereit, die zum Verbinden der Komponenten eines Dokuments mit der Ansicht seiner Daten verwendet werden. Sie müssen nur `CCreateContext` verwendet werden, wenn Sie Teile des Erstellungsprozesses überschreiben.

Eine `CCreateContext` Struktur enthält Zeiger auf das Dokument, das Rahmenfenster, die Ansicht und die Dokumentvorlage. Es enthält auch einen `CRuntimeClass` Zeiger auf eine, die den Typ der zu erstellenden Ansicht identifiziert. Die Laufzeitklasseninformationen und der aktuelle Dokumentzeiger werden verwendet, um eine neue Ansicht dynamisch zu erstellen. In der folgenden Tabelle `CCreateContext` wird beschrieben, wie und wann jedes Element verwendet werden kann:

|Member|type|Wofür ist es für|
|------------|----------|--------------------|
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass`der neuen Ansicht zu erstellen.|
|`m_pCurrentDoc`|`CDocument*`|Das vorhandene Dokument, das der neuen Ansicht zugeordnet werden soll.|
|`m_pNewDocTemplate`|`CDocTemplate*`|Die Dokumentvorlage, die der Erstellung eines neuen MDI-Rahmenfensters zugeordnet ist.|
|`m_pLastView`|`CView*`|Die ursprüngliche Ansicht, der zusätzliche Ansichten modelliert werden, wie bei der Erstellung von Splitterfensteransichten oder beim Erstellen einer zweiten Ansicht in einem Dokument.|
|`m_pCurrentFrame`|`CFrameWnd*`|Das Rahmenfenster, auf dem zusätzliche Rahmenfenster modelliert sind, wie bei der Erstellung eines zweiten Rahmenfensters in einem Dokument.|

Wenn eine Dokumentvorlage ein Dokument und die zugehörigen Komponenten `CCreateContext` erstellt, werden die in der Struktur gespeicherten Informationen überprüft. Beispielsweise sollte eine Ansicht nicht für ein nicht vorhandenes Dokument erstellt werden.

> [!NOTE]
> Alle Zeiger in `CCreateContext` sind optional und `NULL` können, wenn nicht angegeben oder unbekannt sein.

`CCreateContext`wird von den Memberfunktionen verwendet, die unter "Siehe auch" aufgeführt sind. In den Beschreibungen dieser Funktionen finden Sie spezifische Informationen, wenn Sie diese überschreiben möchten.

Hier sind einige allgemeine Richtlinien:

- Wenn der Create-Kontext als Argument `CWnd::Create` `CFrameWnd::Create`für `CFrameWnd::LoadFrame`die Fenstererstellung übergeben wird, wie in , und , gibt der Create-Kontext an, mit dem das neue Fenster verbunden werden soll. Für die meisten Fenster ist die `NULL` gesamte Struktur optional und ein Zeiger kann übergeben werden.

- Bei überschreibbaren Memberfunktionen, `CFrameWnd::OnCreateClient` `CCreateContext` z. B. , ist das Argument optional.

- Für Elementfunktionen, die an der Ansichtserstellung beteiligt sind, müssen Sie genügend Informationen bereitstellen, um die Ansicht zu erstellen. Für die erste Ansicht in einem Splitterfenster müssen Sie beispielsweise die Ansichtsklasseninformationen und das aktuelle Dokument angeben.

Wenn Sie die Framework-Standardwerte verwenden, `CCreateContext`können Sie im Allgemeinen ignorieren. Wenn Sie fortgeschrittenere Änderungen versuchen, führen Sie der Quellcode der Microsoft Foundation-Klassenbibliothek oder die Beispielprogramme, z. B. VIEWEX, an. Wenn Sie einen erforderlichen Parameter vergessen, wird Ihnen eine Framework-Assertion mitteilen, was Sie vergessen haben.

Weitere Informationen `CCreateContext`zu finden Sie im MFC-Beispiel [VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="requirements"></a>Anforderungen

**Kopf:** afxext.h

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd::Erstellen](../../mfc/reference/cframewnd-class.md#create)<br/>
[CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)<br/>
[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)<br/>
[CSplitterWnd::Erstellen](../../mfc/reference/csplitterwnd-class.md#create)<br/>
[CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)<br/>
[CWnd::Create](../../mfc/reference/cwnd-class.md#create)
