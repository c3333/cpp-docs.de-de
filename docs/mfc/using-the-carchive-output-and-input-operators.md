---
title: Verwenden der CArchive-&lt;&lt; und &gt;&gt;-Operatoren
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 8e175f35f2218341c69571c818711596180df4a6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442171"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>Verwenden der CArchive-&lt;&lt; und &gt;&gt;-Operatoren

`CArchive` bietet <\< und > > Operatoren zum Schreiben und Lesen von einfachen Datentypen sowie zum `CObject`s in und aus einer Datei.

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>So speichern Sie ein Objekt in einer Datei über ein Archiv

1. Im folgenden Beispiel wird gezeigt, wie ein Objekt in einer Datei über ein Archiv gespeichert wird:

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>So laden Sie ein Objekt aus einem zuvor in einer Datei gespeicherten Wert

1. Im folgenden Beispiel wird gezeigt, wie ein Objekt aus einem zuvor in einer Datei gespeicherten Wert geladen wird:

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

In der Regel speichern und laden Sie Daten in und aus einer Datei über ein Archiv in den `Serialize` Funktionen `CObject`von abgeleiteten Klassen, die Sie mit dem DECLARE_SERIALIZE-Makro deklarieren müssen. Ein Verweis auf ein `CArchive` Objekt wird an Ihre `Serialize`-Funktion übermittelt. Sie können die `IsLoading`-Funktion des `CArchive`-Objekts aufrufen, um zu bestimmen, ob die `Serialize`-Funktion aufgerufen wurde, um Daten aus der Datei zu laden oder Daten in die Datei zu speichern.

Die `Serialize` Funktion einer serialisierbaren `CObject`abgeleiteten Klasse weist in der Regel die folgende Form auf:

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

Die obige Code Vorlage ist exakt identisch mit der von AppWizard erstellten `Serialize`-Funktion des Dokuments (eine Klasse, die von `CDocument`abgeleitet ist). Diese Code Vorlage hilft Ihnen, Code zu schreiben, der leichter zu überprüfen ist, da der speichernde Code und der Lade Code immer parallel sein sollten, wie im folgenden Beispiel gezeigt:

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

Die Bibliothek definiert **<\<** und **>>** Operatoren für `CArchive` als ersten Operanden und die folgenden Datentypen und Klassentypen als zweiter Operand:

||||
|-|-|-|
|`CObject*`|**Größe** und `CSize`|**float**|
|**WORD**|`CString`|**Punkt** und `CPoint`|
|`DWORD`|**BYTE**|`RECT` und `CRect`|
|**Double**|**LONG**|`CTime` und `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
>  Das Speichern und Laden von `CObject`s über ein Archiv erfordert zusätzliche Überlegungen. Weitere Informationen finden Sie unter [Speichern und Laden von CObjects über ein Archiv](../mfc/storing-and-loading-cobjects-via-an-archive.md).

Die **CArchive-<\<** -und **>>** -Operatoren geben immer einen Verweis auf das `CArchive` Objekt zurück, das der erste Operand ist. Dies ermöglicht es Ihnen, die Operatoren zu verketten, wie unten dargestellt:

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>Weitere Informationen

[Serialisierung: Serialisieren eines Objekts](../mfc/serialization-serializing-an-object.md)
