---
title: Linkertoolwarnung LNK4099
ms.date: 11/04/2016
f1_keywords:
- LNK4099
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
ms.openlocfilehash: b1f330924b8e47e0649268142106a050c83cb20a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183318"
---
# <a name="linker-tools-warning-lnk4099"></a>Linkertoolwarnung LNK4099

PDB ' Dateiname ' wurde mit ' Object/Library ' oder ' Path ' nicht gefunden. Objekt wird verknüpft, als ob keine Debuginformationen

Der Linker konnte die PDB-Datei nicht finden. Kopieren Sie die Datei in das Verzeichnis, das `object/library`enthält.

So suchen Sie den Namen der PDB-Datei, die der Objektdatei zugeordnet ist:

1. Extrahieren Sie eine Objektdatei aus der Bibliothek mit [lib](../../build/reference/lib-reference.md) **/extract:** `objectname` **. obj** `xyz` **. lib**.

1. Überprüfen Sie den Pfad zur PDB-Datei mit **(dumpbin/section:. Debug $ T/rawData** `objectname` **. obj**.

Sie können auch mit [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)kompilieren, sodass die PDB nicht verwendet werden muss, oder Sie können die Option [/Debug](../../build/reference/debug-generate-debug-info.md) Linker entfernen, wenn Sie keine PDB-Dateien für die verknüpften Objekte haben.
