---
title: Schwerwiegender Fehler C1900
ms.date: 11/04/2016
f1_keywords:
- C1900
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
ms.openlocfilehash: 6a802928315126b72397ba6e8cc61b66f46deb41
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202839"
---
# <a name="fatal-error-c1900"></a>Schwerwiegender Fehler C1900

> Il-Konflikt zwischen "*Tool1*", Version "*Zahl1*" und "*Tool2*", Version "*Zahl2*"

In verschiedenen Durchläufen des Compilers ausgeführte Tools stimmen nicht überein. *Zahl1* und *Zahl2* verweisen auf die Datumsangaben für die Dateien. Z. B. führt in Durchgang 1 durch das Compiler-front End (c1.dll) ausgeführt und in Durchgang 2 führt der Compiler-back-End (c2.dll) aus. Die Datumsangaben der Dateien müssen übereinstimmen.

Um dieses Problem zu beheben, stellen Sie sicher, dass alle Aktualisierungen auf Visual Studio angewendet wurden. Wenn das Problem weiterhin besteht, verwenden Sie **Programme und Funktionen** in der Windows-Systemsteuerung, um Visual Studio zu reparieren oder neu zu installieren.
