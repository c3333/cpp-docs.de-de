---
title: Befehlshandler für das Scrollen von Datensätzen (MFC-Datenzugriff)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 8bbacd6625e846381d2bafc8133e8b36efe51b1a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213446"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>Befehlshandler für das Scrollen von Datensätzen (MFC-Datenzugriff)

Die [CRecordView](../mfc/reference/crecordview-class.md) -Klasse stellt die standardmäßige Befehls Behandlung für die folgenden Standard Befehle bereit:

- ID_RECORD_MOVE_FIRST

- ID_RECORD_MOVE_LAST

- ID_RECORD_MOVE_NEXT

- ID_RECORD_MOVE_PREV

Die `OnMove` Member-Funktion bietet standardmäßige Befehls Behandlung für alle vier Befehle, die von Datensatz zu Datensatz wechseln. Nachdem diese Befehle ausgegeben wurden, lädt RFX (oder DFX) den neuen Datensatz in die Recordset-Felder, und DDX verschiebt die Werte in die Steuerelemente des Datensatzformulars. Weitere Informationen zu RFX finden Sie unter [Daten Satz Feld Austausch (RFX)](../data/odbc/record-field-exchange-rfx.md).

> [!NOTE]
>  Verwenden Sie diese Standardbefehls-IDs für alle Benutzeroberflächenobjekte, die den standardmäßigen Navigationsbefehlen des Datensatzes zugeordnet sind.

## <a name="see-also"></a>Weitere Informationen

[Unterstützen der Navigation in einer Daten Satz Ansicht](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)
