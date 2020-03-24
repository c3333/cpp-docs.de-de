---
title: Linkertoolwarnung LNK4014
ms.date: 11/04/2016
f1_keywords:
- LNK4014
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
ms.openlocfilehash: 5de53abc2342e3ed743f6b4abb871e05606dfc37
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194277"
---
# <a name="linker-tools-warning-lnk4014"></a>Linkertoolwarnung LNK4014

Member-Objekt "ObjectName" kann nicht gefunden werden.

LIB konnte `objectname` in der Bibliothek nicht finden.

Die Optionen **/Remove** und **/extract** erfordern den vollständigen Namen des Member-Objekts, das gelöscht oder in eine Datei kopiert werden soll. Der vollständige Name enthält den Pfad der ursprünglichen Objektdatei. Um die vollständigen Namen von Element Objekten in einer Bibliothek anzuzeigen, verwenden Sie DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) oder lib [/List](../../build/reference/managing-a-library.md).
