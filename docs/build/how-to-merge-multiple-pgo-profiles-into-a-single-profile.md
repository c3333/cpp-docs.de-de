---
title: 'Vorgehensweise: Zusammenführen mehrerer PGO-Profile in einem einzigen Profil'
ms.date: 03/14/2018
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
ms.openlocfilehash: 451c0f30a271f5dce3974e172766da4a23340b93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188872"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Vorgehensweise: Zusammenführen mehrerer PGO-Profile in einem einzigen Profil

Die profilgesteuerte Optimierung (PGO) ist ein hervorragendes Tool für die Erstellung optimierter Binärdateien auf der Grundlage eines Szenarios mit einem Profil. Aber was ist, wenn Ihre Anwendung mehrere wichtige, aber unterschiedliche Szenarios umfasst? Wie können Sie ein einzelnes Profil erstellen, das von PGO in verschiedenen Szenarios verwendet werden kann? In Visual Studio übernimmt der PGO-Manager, [pgomgr.exe](pgomgr.md), diese Aufgabe für Sie.

Die Syntax für das Zusammenführen von Profilen lautet:

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

Dabei ist `num` eine optionale Gewichtung für die PGC-Dateien, die von diesem Merge hinzugefügt werden. Gewichtungen werden häufig verwendet, wenn einige Szenarios wichtiger sind als andere, oder wenn Szenarios vorhanden sind, die mehrmals ausgeführt werden sollen.

> [!NOTE]
> Der PGO-Manager funktioniert nicht mit veralteten Profildaten. Um eine PGC-Datei in einer PGD-Datei zusammenzuführen, muss die PGC-Datei von einer ausführbaren Datei generiert werden, die durch denselben Linkaufruf erstellt wurde, der die PGD-Datei generiert hat.

## <a name="examples"></a>Beispiele

In diesem Beispiel fügt der PGO-Manager „pgcFile.pgc“ sechsmal zu „pgdFile.pgd“ hinzu:

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

In diesem Beispiel fügt der PGO-Manager „pgcFile1.pgc“ und „pgcFile2.pgc“ zweimal pro PGC-Datei zu „pgdFile.pgd“ hinzu:

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

Wenn der PGO-Manager ohne PGC-Dateiargumente ausgeführt wird, durchsucht er das lokale Verzeichnis nach allen PGC-Dateien, die denselben Basisnamen wie die PGD-Datei gefolgt von einem Ausrufezeichen (!) und einem oder mehreren beliebigen Zeichen aufweisen. Wenn das lokale Verzeichnis beispielsweise die Dateien „test.pgd“, „test!1.pgc“, „test2.pgc“ und „test!hello.pgc“ enthält und der folgende Befehl aus dem lokalen Verzeichnis ausgeführt wird, führt **pgomgr** die Dateien „test!1.pgc“ und „test!hello.pgc“ in „test.pgd“ zusammen.

`pgomgr /merge test.pgd`

## <a name="see-also"></a>Siehe auch

[Profilgesteuerte Optimierungen](profile-guided-optimizations.md)
