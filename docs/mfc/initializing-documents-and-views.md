---
title: Initialisieren von Dokumenten und Ansichten
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
ms.openlocfilehash: 0e970d6e8a166283f82575b309cf023f48899403
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626353"
---
# <a name="initializing-documents-and-views"></a>Initialisieren von Dokumenten und Ansichten

Dokumente werden auf zwei verschiedene Arten erstellt, sodass die Dokument Klasse beide Methoden unterstützen muss. Zuerst kann der Benutzer ein neues, leeres Dokument mit dem Datei neuen Befehl erstellen. Initialisieren Sie in diesem Fall das Dokument in der Überschreibung der [OnNewDocument](reference/cdocument-class.md#onnewdocument) -Member-Funktion der [CDocument](reference/cdocument-class.md)-Klasse. Zweitens kann der Benutzer den Befehl Öffnen im Menü Datei verwenden, um ein neues Dokument zu erstellen, dessen Inhalt aus einer Datei gelesen wird. Initialisieren Sie in diesem Fall das Dokument in der Überschreibung der [OnOpenDocument](reference/cdocument-class.md#onopendocument) -Member-Funktion der-Klasse `CDocument` . Wenn beide Initialisierungen identisch sind, können Sie eine gemeinsame Member-Funktion sowohl von über schreibungen als auch von `OnOpenDocument` aufgerufen werden, `OnNewDocument` um ein sauberes Dokument zu initialisieren und dann den Öffnungsvorgang abzuschließen.

Sichten werden erstellt, nachdem Ihre Dokumente erstellt wurden. Die beste Zeit zum Initialisieren einer Ansicht ist, nachdem das Framework das Erstellen von Dokument, Rahmen Fenster und Ansicht abgeschlossen hat. Sie können Ihre Ansicht initialisieren, indem Sie die [OnInitialUpdate](reference/cview-class.md#oninitialupdate) -Member-Funktion von [CView](reference/cview-class.md)überschreiben. Wenn Sie jedes Mal, wenn das Dokument geändert wird, etwas neu initialisieren oder anpassen müssen, können Sie [OnUpdate](reference/cview-class.md#onupdate)überschreiben.

## <a name="see-also"></a>Siehe auch

[Initialisieren und Bereinigen von Dokumenten und Ansichten](initializing-and-cleaning-up-documents-and-views.md)
