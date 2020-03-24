---
title: Ressourcen Bezeichner (Symbole) (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.identifiers
helpviewer_keywords:
- symbols [C++], resource identifiers
- symbols [C++], creating
- resource symbols
- symbols [C++], editing
- resource editors [C++], resource symbols
ms.assetid: 8fccc09a-0237-4a65-b9c4-57d60c59e324
ms.openlocfilehash: ba0958e455557660ef704f1c2fa570d46307082f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214395"
---
# <a name="resource-identifiers-symbols-c"></a>Ressourcen Bezeichner (Symbole) (C++)

Ein Symbol ist ein Ressourcen Bezeichner (ID), der aus zwei Teilen besteht, einem Symbolnamen (Text Zeichenfolge), der einem Symbolwert (Integer) zugeordnet ist, z. b.:

```
IDC_EDITNAME = 5100
```

Symbolnamen werden meistens als Bezeichner bezeichnet.

Symbole bieten eine anschauliche Möglichkeit, auf Ressourcen und Objekte der Benutzeroberfläche zu verweisen, sowohl im Quellcode als auch bei der Arbeit im Ressourcen-Editor. Mithilfe des Dialogfelds [Ressourcensymbole](../windows/viewing-resource-symbols.md)können Symbole komfortabel an einem Ort angezeigt und bearbeitet werden.

In dem Maß, in dem Ihre Anwendung in Umfang und Komplexität wächst, wächst auch die Anzahl ihrer Ressourcen und Symbole. Das Nachverfolgen einer großen Zahl von Symbolen, die über verschiedene Dateien verteilt sind, kann schwierig sein. Das Dialogfeld **Ressourcen Symbole** vereinfacht die Symbol Verwaltung, indem es ein zentrales Tool bietet, über das Sie folgende Aufgaben ausführen können:

- [Symbole erstellen](../windows/creating-new-symbols.md)

- [Symbole verwalten](../windows/changing-a-symbol-or-symbol-name-id.md)

- [Anzeigen vordefinierter Symbol-IDs](../windows/predefined-symbol-ids.md)

Wenn Sie eine neue Ressource oder ein neues Ressourcenobjekt erstellen, stellt der [Ressourcen-Editor](../windows/resource-editors.md) einen Standardnamen für die Ressource bereit, z. B. `IDC_RADIO1`, und weist ihr einen Wert zu. Die Name-Plus-Wert-Definition wird in der `Resource.h`-Datei gespeichert.

> [!NOTE]
> Wenn Sie Ressourcen oder Ressourcenobjekte aus einer RC-Datei in eine andere kopieren, ändert Visual C++ möglicherweise den Symbolwert der übertragenen Ressource, oder den Symbolnamen und den Wert, um Konflikte mit Symbolnamen oder Werten in der vorhandenen Datei zu vermeiden.

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Arbeiten mit Ressourcendateien](../windows/working-with-resource-files.md)<br/>
[Ressourcendateien](../windows/resource-files-visual-studio.md)<br/>
[Ressourcen-Editor](../windows/resource-editors.md)<br/>
