---
title: Features von Datensatzansichts-Klassen (MFC-Datenzugriff)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
ms.openlocfilehash: 62597a3eb3f7a7e779ca57c9781565176df568d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213433"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Features von Datensatzansichts-Klassen (MFC-Datenzugriff)

Sie können eine Formular basierte Datenzugriffs Programmierung mit der [CFormView](../mfc/reference/cformview-class.md)-Klasse durchführen, aber [CRecordView](../mfc/reference/crecordview-class.md) ist in der Regel eine bessere Klasse, von der abgeleitet werden kann. Zusätzlich zu den `CFormView` Features `CRecordView`:

- Stellt einen Dialog Datenaustausch (DDX) zwischen den Formular Steuerelementen und dem zugeordneten Recordset-Objekt bereit.

- Handles werden zuerst verschoben, vorwärts verschieben, vorherige und letzte Befehle verschieben, um durch die Datensätze im zugeordneten Recordset-Objekt zu navigieren.

- Aktualisiert Änderungen am aktuellen Datensatz, wenn der Benutzer zu einem anderen Datensatz wechselt.

Weitere Informationen zur Navigation finden Sie unter [Daten Satz Ansichten: unterstützen der Navigation in einer Daten Satz Ansicht](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).

## <a name="see-also"></a>Weitere Informationen

[Datensatzansichten (MFC-Datenzugriff)](../data/record-views-mfc-data-access.md)<br/>
[Liste der ODBC-Treiber](../data/odbc/odbc-driver-list.md)
