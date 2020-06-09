---
title: Ableiten einer Dokumentklasse von CDocument
ms.date: 11/04/2016
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
ms.openlocfilehash: 399230446977636cc8769efe32b8f86fad466b83
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616117"
---
# <a name="deriving-a-document-class-from-cdocument"></a>Ableiten einer Dokumentklasse von CDocument

Dokumente enthalten und verwalten die Daten Ihrer Anwendung. Gehen Sie folgendermaßen vor, um die vom MFC-Anwendungs-Assistenten bereitgestellte Dokument Klasse zu verwenden:

- Leiten Sie eine Klasse von `CDocument` für jeden Dokumenttyp ab.

- Fügen Sie Element Variablen zum Speichern der einzelnen Dokument Daten hinzu.

- Über `CDocument` schreiben `Serialize` Sie die Member-Funktion in der Document-Klasse. `Serialize`schreibt und liest die Daten des Dokuments in und von der Festplatte.

## <a name="other-document-functions-often-overridden"></a>Andere Dokument Funktionen, die häufig überschrieben werden

Möglicherweise möchten Sie auch andere Element `CDocument` Funktionen überschreiben. Insbesondere müssen Sie " [OnNewDocument](reference/cdocument-class.md#onnewdocument) " und " [OnOpenDocument](reference/cdocument-class.md#onopendocument) " häufig überschreiben, um die Datenmember des Dokuments zu initialisieren, und " [deletecontent](reference/cdocument-class.md#deletecontents) ", um dynamisch zugeordnete Daten zu zerstören. Informationen zu über schreibbaren Membern finden Sie unter Class [CDocument](reference/cdocument-class.md) in der *MFC-Referenz*.

## <a name="see-also"></a>Siehe auch

[Verwenden von Dokumenten](using-documents.md)
