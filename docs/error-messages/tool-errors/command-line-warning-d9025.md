---
title: Befehlszeilenwarnung D9025
ms.date: 11/04/2016
f1_keywords:
- D9025
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
ms.openlocfilehash: 4afd4d4dc07ffaae6038c025ee371278ebbebea6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196715"
---
# <a name="command-line-warning-d9025"></a>Befehlszeilenwarnung D9025

Überschreiben von "Option1" mit "option2"

Die *Option1* -Option wurde angegeben, aber von *Option2*überschrieben. Die *Option2* -Option wurde verwendet.

Wenn zwei Optionen widersprüchliche oder nicht kompatible Anweisungen angeben, wird die Anweisung verwendet, die in der Option in der-Option am weitesten rechts in der Befehlszeile angegeben oder impliziert ist.

Wenn Sie diese Warnung erhalten, wenn Sie eine Kompilierung aus der Entwicklungsumgebung durchlaufen und nicht sicher sind, woher die in Konflikt stehenden Optionen kommen, sollten Sie Folgendes beachten:

- Eine Option kann entweder im Code oder in den Projekteinstellungen des Projekts angegeben werden. Wenn Sie die [Befehlszeilen-Eigenschaften Seiten](../../build/reference/command-line-property-pages.md) des Compilers betrachten und die in Konflikt stehenden Optionen im Feld **alle Optionen** angezeigt werden, werden die Optionen in den Eigenschaften Seiten des Projekts festgelegt. andernfalls werden die Optionen im Quellcode festgelegt.

   Wenn die Optionen in den Eigenschaften Seiten des Projekts festgelegt sind, überprüfen Sie die präprozessoreigenschaftenseite des Compilers (wobei der Projekt Knoten im Projektmappen-Explorer ausgewählt ist).  Wenn die Option nicht festgelegt ist, überprüfen Sie die Einstellungen der präprozessoreigenschaftenseite für jede Quell Code Datei (in Projektmappen-Explorer), um sicherzustellen, dass Sie nicht hinzugefügt wird.

   Wenn die Optionen im Code festgelegt werden, können Sie entweder im Code oder in den Windows-Headern festgelegt werden.  Möglicherweise versuchen Sie, eine vorverarbeitete Datei ([/P](../../build/reference/p-preprocess-to-a-file.md)) zu erstellen und nach dem Symbol zu suchen.
