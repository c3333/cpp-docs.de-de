---
title: 'Ressourcencompiler: Fehler RC2144'
ms.date: 11/04/2016
f1_keywords:
- RC2144
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
ms.openlocfilehash: 1b080916642fc1be4b22820668c4cb4137675425
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191196"
---
# <a name="resource-compiler-error-rc2144"></a>Ressourcencompiler: Fehler RC2144

Primäre Sprach-ID ist keine Zahl

Primäre Sprach-ID muss eine hexadezimale Sprachen-ID sein. Unter [Sprach- und Länder-/Regionen-Strings](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) in der *Laufzeit-Bibliothek-Referenz* finden Sie eine Liste der gültigen Sprach-IDs.

Dieser Fehler kann auch auftreten, wenn Sie Ressourcen hinzugefügt und aus der.RC-Datei mithilfe des Tools gelöscht haben. Um dieses Problem zu beheben, öffnen Sie die.RC-Datei in einem Texteditor und bereinigen Sie manuell alle nicht verwendeten Ressourcen.
