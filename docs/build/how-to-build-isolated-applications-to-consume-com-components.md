---
title: 'Vorgehensweise: Erstellen von isolierten Anwendungen zur Verwendung von COM-Komponenten'
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
ms.openlocfilehash: 8ae3c51502267f202cbb85ea7be2a81dc3310410
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493236"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Vorgehensweise: Erstellen von isolierten Anwendungen zur Verwendung von COM-Komponenten

Isolierte Anwendungen sind Anwendungen, deren Manifeste in das Programm integriert sind. Sie können isolierte Anwendungen zur Verwendung von COM-Komponenten erstellen.

### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Hinzufügen von COM-Verweisen zu Manifesten von isolierten Anwendungen

1. Öffnen Sie die Seite mit den Projekteigenschaften für die isolierte Anwendung.

1. Erweitern Sie zunächst den Knoten **Konfigurationseigenschaften** und anschließend den Knoten **Manifesttool**.

1. Navigieren Sie zur Seite mit den **Isolated COM**-Eigenschaften, und legen Sie die Eigenschaft **Komponentendateiname** auf den Namen der COM-Komponente fest, die von der isolierten Anwendung verwendet werden soll.

1. Klicken Sie auf **OK**.

### <a name="to-build-manifests-into-isolated-applications"></a>Erstellen von Manifesten in isolierten Anwendungen

1. Öffnen Sie die Seite mit den Projekteigenschaften für die isolierte Anwendung.

1. Erweitern Sie zunächst den Knoten **Konfigurationseigenschaften** und anschließend den Knoten **Manifesttool**.

1. Klicken Sie auf die Eigenschaftenseite **Eingabe und Ausgabe**, und legen Sie dann die Eigenschaft **Manifest einbetten** auf **Ja** fest.

1. Klicken Sie auf **OK**.

1. Erstellen Sie die Projektmappe.

## <a name="see-also"></a>Siehe auch

[Isolierte Anwendungen](/windows/win32/SbsCs/isolated-applications)<br/>
[Informationen zu parallelen Assemblys](/windows/win32/SbsCs/about-side-by-side-assemblies-)
