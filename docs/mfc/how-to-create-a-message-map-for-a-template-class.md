---
title: 'Gewusst wie: Erstellen einer Meldungszuordnung für eine Vorlagenklasse'
ms.date: 11/04/2016
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
ms.openlocfilehash: 65ddc77b4e8fd466c7d651e54e93a504b4858da1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620064"
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>Gewusst wie: Erstellen einer Meldungszuordnung für eine Vorlagenklasse

Die Nachrichten Zuordnung in MFC bietet eine effiziente Möglichkeit zum Weiterleiten von Windows-Meldungen an eine entsprechende C++-Objektinstanz. Beispiele für MFC-Nachrichten Zuordnungs Ziele sind Anwendungs Klassen, Dokument-und Ansichts Klassen, Steuerelement Klassen usw.

Herkömmliche MFC-Nachrichten Zuordnungen werden mit dem [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) -Makro deklariert, um den Anfang der Meldungs Zuordnung zu deklarieren, einen Makro Eintrag für jede Methode der Nachrichten Handler-Klasse und schließlich das [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) Makro, um das Ende der Meldungs Zuordnung zu deklarieren.

Eine Einschränkung mit dem [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) -Makro tritt auf, wenn Sie in Verbindung mit einer Klasse verwendet wird, die Vorlagen Argumente enthält. Bei Verwendung mit einer Vorlagen Klasse verursacht dieses Makro einen Kompilierzeitfehler aufgrund der fehlenden Vorlagen Parameter während der Makro Erweiterung. Das [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map) -Makro wurde so entworfen, dass Klassen, die ein einzelnes Vorlagen Argument enthalten, ihre eigenen Meldungs Zuordnungen deklarieren können.

## <a name="example"></a>Beispiel

Sehen Sie sich ein Beispiel an, in dem die MFC- [CListBox](reference/clistbox-class.md) -Klasse erweitert wird, um die Synchronisierung mit einer externen Datenquelle Die fiktive `CSyncListBox` Klasse wird wie folgt deklariert:

[!code-cpp[NVC_MFC_CListBox#42](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]

Die- `CSyncListBox` Klasse wird auf einem einzelnen Typ, der die Datenquelle beschreibt, mit der Sie synchronisiert wird, auf Vorlagen basieren. Außerdem werden drei Methoden deklariert, die an der Meldungs Zuordnung der-Klasse beteiligt `OnPaint` sind:, `OnDestroy` und `OnSynchronize` . Die- `OnSynchronize` Methode wird wie folgt implementiert:

[!code-cpp[NVC_MFC_CListBox#43](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]

Die obige Implementierung ermöglicht es, `CSyncListBox` dass die-Klasse auf jeden Klassentyp spezialisiert wird, der die- `GetCount` Methode implementiert, z `CArray` . b., `CList` und `CMap` . Die- `StringizeElement` Funktion ist eine Vorlagen Funktion, die mit folgendem prototyptypisiert wird:

[!code-cpp[NVC_MFC_CListBox#44](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]

Normalerweise würde die Meldungs Zuordnung für diese Klasse folgendermaßen definiert werden:

```cpp
BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)
  ON_WM_PAINT()
  ON_WM_DESTROY()
  ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)
END_MESSAGE_MAP()
```

Dabei ist **LBN_SYNCHRONIZE** eine benutzerdefinierte Benutzer Nachricht, die von der Anwendung definiert wird, z. b.:

[!code-cpp[NVC_MFC_CListBox#45](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]

Die obige Makro Zuordnung wird aufgrund der Tatsache, dass die Vorlagen Spezifikation für die `CSyncListBox` Klasse während der Makro Erweiterung fehlt, nicht kompiliert. Das **BEGIN_TEMPLATE_MESSAGE_MAP** -Makro löst dies durch Einbeziehen des angegebenen Vorlagen Parameters in die erweiterte Makro Zuordnung. Die Meldungs Zuordnung für diese Klasse lautet wie folgt:

[!code-cpp[NVC_MFC_CListBox#46](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]

Im folgenden Beispiel wird die Verwendung der- `CSyncListBox` Klasse mithilfe eines- `CStringList` Objekts veranschaulicht:

[!code-cpp[NVC_MFC_CListBox#47](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]

Um den Test abzuschließen, `StringizeElement` muss die Funktion für die Arbeit mit der- `CStringList` Klasse spezialisiert sein:

[!code-cpp[NVC_MFC_CListBox#48](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]

## <a name="see-also"></a>Siehe auch

[BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)<br/>
[Meldungsbehandlung und Zuordnung](message-handling-and-mapping.md)
