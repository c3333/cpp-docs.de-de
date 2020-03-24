---
title: Benutzeroberflächen-Aktualisierung für Datensatzansichten (MFC-Datenzugriff)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces, updating
- menus, updating as context changes
- record views, user interface
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
ms.openlocfilehash: 9bfb907d21c928c605b304c595acb834d0046e35
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209052"
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>Benutzeroberflächen-Aktualisierung für Datensatzansichten (MFC-Datenzugriff)

`CRecordView` stellt Standard-Benutzeroberflächen-Update Handler für die Navigations Befehle bereit. Diese Handler automatisieren die Aktivierung und Deaktivierung der Benutzeroberflächenobjekte – Menüelemente und Symbolleisten-Schaltflächen. Der Anwendungs-Assistent bietet Standardmenüs und, wenn Sie die Option **andockbare Symbolleiste** auswählen, eine Reihe von Symbolleisten-Schaltflächen für die Befehle. Wenn Sie eine Datensatzansichtsklasse mithilfe von `CRecordView` erstellen, können Sie der Anwendung vergleichbare Benutzeroberflächenobjekte hinzufügen.

### <a name="to-create-menu-resources-with-the-menu-editor"></a>So erstellen Sie Menüressourcen mit dem Menü-Editor

1. Wenn Sie auf die Informationen zur Verwendung des [Menü-Editors](../windows/menu-editor.md)verweisen, erstellen Sie ein eigenes Menü mit denselben vier Befehlen.

#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>So erstellen Sie Symbolleisten-Schaltflächen mit dem Grafik-Editor

1. Wenn Sie die Informationen zur Verwendung des [Symbol](../windows/toolbar-editor.md)leisten-Editors verwenden, bearbeiten Sie die Symbolleisten Ressource, um Symbolleisten Schaltflächen für die Navigations Befehle des Datensatzes

## <a name="see-also"></a>Weitere Informationen

[Unterstützen der Navigation in einer Daten Satz Ansicht](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)<br/>
[Verwenden einer Daten Satz Ansicht](../data/using-a-record-view-mfc-data-access.md)
