---
title: Formularansichten (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces [MFC], forms
- forms [MFC]
- applications [MFC], forms-based
- forms-based applications [MFC]
- forms [MFC], adding to applications
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
ms.openlocfilehash: 5e8912c9013175fe254b2f4a4a968a67fd071f39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365295"
---
# <a name="form-views-mfc"></a>Formularansichten (MFC)

Sie können Formulare zu jeder Visual C++-Anwendung hinzufügen, die die MFC-Bibliotheken unterstützt, einschließlich einer [formularbasierten Anwendung](../mfc/reference/creating-a-forms-based-mfc-application.md) (eine Anwendung, deren Ansichtsklasse von `CFormView`abgeleitet ist). Wenn Sie Ihre Anwendung zunächst nicht zur Unterstützung von Formularen erstellt haben, fügt Visual C++ diese Unterstützung für Sie hinzu, wenn Sie ein neues Formular einfügen. In einer SDI- oder MDI-Anwendung, die die [Standarddokument-/Ansichtsarchitektur](../mfc/document-view-architecture.md)implementiert, wenn der Benutzer den Befehl **Neu** (standardmäßig im Menü **Datei)** wählt, fordert Visual C++ den Benutzer auf, aus den verfügbaren Formularen auszuwählen.

Wenn der Benutzer bei einer SDI-Anwendung den Befehl **Neu** auswählt, wird die aktuelle Instanz des Formulars weiterhin ausgeführt, aber eine neue Instanz der Anwendung mit dem ausgewählten Formular wird erstellt, wenn keine Instanz gefunden wird. In einer MDI-Anwendung wird die aktuelle Instanz des Formulars weiterhin ausgeführt, wenn der Benutzer den Befehl **Neu** auswählt.

> [!NOTE]
> Sie können ein Formular in eine dialogbasierte Anwendung einfügen `CDialog` (eine, deren Dialogklasse basiert und eine, in der keine Ansichtsklasse implementiert ist). Ohne die Dokument-/Ansichtsarchitektur implementiert Visual C++ jedoch nicht automatisch die **Datei&#124;** **Neue** Funktionalität. Sie müssen eine Möglichkeit für den Benutzer erstellen, zusätzliche Formulare anzuzeigen, z. B. durch Implementieren eines Dialogfelds mit Registerkarten mit verschiedenen Eigenschaftenseiten.

Wenn Sie ein neues Formular in Ihre Anwendung einfügen, führt Visual C++ die folgenden Schritte aus:

- Erstellt eine Klasse basierend auf einer der von`CFormView`Ihnen `CRecordView` `CDaoRecordView`auswählen `CDialog`Klassen im Formularstil ( , , , oder ).

- Erstellt eine Dialogressource mit entsprechenden Formatvorlagen (oder Sie können eine vorhandene Dialogfeldressource verwenden, die noch keiner Klasse zugeordnet ist).

   Wenn Sie eine vorhandene Dialogfeldressource auswählen, müssen Sie diese Formatvorlagen möglicherweise mithilfe der Eigenschaftenseite für das Dialogfeld festlegen. Stile für ein Dialogfeld müssen Folgendes enthalten:

     **WS_CHILD**=Ein

     **WS_BORDER**=Aus

     **WS_VISIBLE**=Aus

     **WS_CAPTION**=Aus

Für Anwendungen, die auf der Dokument-/Ansichtsarchitektur basieren, gilt auch der Befehl **"Neues Formular"** (Rechtsklick in der Klassenansicht):

- Erstellt `CDocument`eine -basierte Klasse

   Anstatt eine neue Klasse erstellen zu lassen, können Sie jede vorhandene -basierte `CDocument`Klasse in Ihrem Projekt verwenden.

- Generiert eine Dokumentvorlage `CDocument`(abgeleitet von ) mit Zeichenfolgen-, Menü- und Symbolressourcen.

   Sie können auch eine neue Klasse erstellen, auf der die Vorlage basieren soll.

- Fügt einen `AddDocumentTemplate` Aufruf im `InitInstance` Code Ihrer Anwendung hinzu.

   Visual C++ fügt diesen Code für jedes neue Formular hinzu, das Sie erstellen, wodurch das Formular der Liste der verfügbaren Formulare hinzugefügt wird, wenn der Benutzer den Befehl **Neu** auswählt. Dieser Code enthält die zugeordnete Ressourcen-ID des Formulars und die Namen der zugeordneten Dokument-, Ansichts- und Frameklassen, aus denen das neue Formularobjekt zusammen besteht.

   Dokumentvorlagen dienen als Verbindung zwischen Dokumenten, Rahmenfenstern und Ansichten. Für ein einzelnes Dokument können Sie viele Vorlagen erstellen.

Weitere Informationen finden Sie unter

- [Erstellen einer formularbasierten Anwendung](../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Einfügen eines Formulars in ein Projekt](../mfc/inserting-a-form-into-a-project.md)

## <a name="see-also"></a>Siehe auch

[Benutzeroberflächenelemente](../mfc/user-interface-elements-mfc.md)
