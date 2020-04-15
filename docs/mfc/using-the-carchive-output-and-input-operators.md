---
title: Verwenden des &lt; &lt; CArchivs und &gt; &gt; der Operatoren
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 91ea565867cc0cb3b27ad9d5597037b637cb6544
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368962"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>Verwenden des &lt; &lt; CArchivs und &gt; &gt; der Operatoren

`CArchive`bietet \< <und >> Operatoren zum Schreiben `CObject`und Lesen einfacher Datentypen sowie s zu und aus einer Datei.

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>So speichern Sie ein Objekt in einer Datei über ein Archiv

1. Das folgende Beispiel zeigt, wie ein Objekt über ein Archiv in einer Datei gespeichert wird:

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>So laden Sie ein Objekt aus einem zuvor in einer Datei gespeicherten Wert

1. Das folgende Beispiel zeigt, wie ein Objekt aus einem zuvor in einer Datei gespeicherten Wert geladen wird:

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

Normalerweise speichern und laden Sie Daten in und aus `Serialize` einer `CObject`Datei über ein Archiv in den Funktionen von -derived-Klassen, die Sie mit dem DECLARE_SERIALIZE-Makro deklariert haben müssen. Ein Verweis `CArchive` auf ein Objekt `Serialize` wird an Ihre Funktion übergeben. Sie rufen `IsLoading` die `CArchive` Funktion des Objekts auf, um zu bestimmen, ob die `Serialize` Funktion aufgerufen wurde, um Daten aus der Datei zu laden oder Daten in die Datei zu speichern.

Die `Serialize` Funktion einer serialisierbaren `CObject`-abgeleiteten Klasse hat in der Regel die folgende Form:

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

Die obige Codevorlage ist genau die gleiche `Serialize` wie die, die AppWizard `CDocument`für die Funktion des Dokuments erstellt (eine von abgeleitete Klasse ). Diese Codevorlage hilft Ihnen beim Schreiben von Code, der einfacher zu überprüfen ist, da der Speichercode und der Ladecode immer parallel sein sollten, wie im folgenden Beispiel:

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

Die Bibliothek ** < ** definiert **>>** und `CArchive` operatoriert als erster Operand und die folgenden Datentypen und Klassentypen als zweiten Operanden:

||||
|-|-|-|
|`CObject*`|**GRÖSSE** und`CSize`|**float**|
|**WORD**|`CString`|**POINT** und`CPoint`|
|`DWORD`|**Byte**|`RECT` und `CRect`|
|**Double**|**Lange**|`CTime` und `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
> Das Speichern `CObject`und Laden von s über ein Archiv erfordert zusätzliche Berücksichtigung. Weitere Informationen finden Sie unter [Speichern und Laden von CObjects über ein Archiv](../mfc/storing-and-loading-cobjects-via-an-archive.md).

Die **CArchive-<\< ** und **>>** Operatoren `CArchive` geben immer einen Verweis auf das Objekt zurück, das der erste Operand ist. Auf diese Weise können Sie die Operatoren verketten, wie unten dargestellt:

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>Siehe auch

[Serialisierung: Serialisieren eines Objekts](../mfc/serialization-serializing-an-object.md)
