---
title: Standardbefehle und Fenster-IDs
ms.date: 11/04/2016
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: a7f9e37702c686e13379d4034be94949f92e5e79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372955"
---
# <a name="standard-command-and-window-ids"></a>Standardbefehle und Fenster-IDs

Die Microsoft Foundation-Klassenbibliothek definiert eine Reihe von Standardbefehls- und Fenster-IDs in Afxres.h. Diese IDs werden am häufigsten in den Ressourcen-Editoren und dem [Klassen-Assistenten](mfc-class-wizard.md) verwendet, um Nachrichten Ihren Handlerfunktionen zuzuordnen. Alle Standardbefehle haben ein **ID_** Präfix. Wenn Sie beispielsweise den Menüeditor verwenden, binden Sie normalerweise das Menüelement "Datei geöffnet" an die Standard-ID_FILE_OPEN Befehls-ID.

Bei den meisten Standardbefehlen muss Anwendungscode nicht auf die Befehls-ID verweisen, da das Framework`CWinThread` `CWinApp`selbst `CView` `CDocument`die Befehle über Nachrichtenzuordnungen in den primären Frameworkklassen ( , , , , usw.) verarbeitet.

Zusätzlich zu den Standardbefehls-IDs werden eine Reihe weiterer Standard-IDs definiert, die das Präfix **AFX_ID**. Diese IDs enthalten Standardfenster-IDs (Präfix **AFX_IDW_**), Zeichenfolgen-IDs (Präfix **AFX_IDS_**) und mehrere andere Typen.

IDs, die mit dem **Präfix AFX_ID** beginnen, werden selten von Programmierern verwendet, aber Sie müssen möglicherweise auf diese IDs verweisen, wenn Frameworkfunktionen überschreiben, die sich auch auf die **AFX_ID**s beziehen.

IDs sind in dieser Referenz nicht einzeln dokumentiert. Weitere Informationen hierzu finden Sie in den Technischen Hinweisen [20](../../mfc/tn020-id-naming-and-numbering-conventions.md), [21](../../mfc/tn021-command-and-message-routing.md)und [22](../../mfc/tn022-standard-commands-implementation.md).

> [!NOTE]
> Die Headerdatei Afxres.h ist indirekt in Afxwin.h enthalten. Sie müssen die folgende Anweisung explizit in die Ressourcenskriptdatei (.rc) Ihrer Anwendung aufnehmen:

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
