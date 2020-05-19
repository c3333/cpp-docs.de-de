---
title: 'Vorgehensweise: Erstellen von COM-Komponenten ohne Registrierung'
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 783677c97835acc98751fc4a19f9405af752b71a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188937"
---
# <a name="how-to-build-registration-free-com-components"></a>Vorgehensweise: Erstellen von COM-Komponenten ohne Registrierung

COM-Komponenten ohne Registrierung sind COM-Komponenten, die über in die DLLs integrierte Manifeste verfügen.

### <a name="to-build-manifests-into-com-components"></a>Erstellen von Manifesten in COM-Komponenten

1. Öffnen Sie die Seite mit den Projekteigenschaften für die COM-Komponente.

1. Erweitern Sie zunächst den Knoten **Konfigurationseigenschaften** und anschließend den Knoten **Manifesttool**.

1. Klicken Sie auf die Eigenschaftenseite **Eingabe und Ausgabe**, und legen Sie dann die Eigenschaft **Manifest einbetten** auf **Ja** fest.

1. Klicken Sie auf **OK**.

1. Erstellen Sie die Projektmappe.

## <a name="see-also"></a>Siehe auch

[How to: Erstellen von isolierten Anwendungen zur Verwendung von COM-Komponenten](how-to-build-isolated-applications-to-consume-com-components.md)
