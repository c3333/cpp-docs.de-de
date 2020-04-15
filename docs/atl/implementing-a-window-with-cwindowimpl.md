---
title: Implementieren eines Fensters mit CWindowImpl
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
ms.openlocfilehash: e5fdbf15ddd7edc69f0667a9b7e08c7c5e531a5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319449"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>Implementieren eines Fensters mit CWindowImpl

Um ein Fenster zu implementieren, `CWindowImpl`leiten Sie eine Klasse von ab. Deklarieren Sie in der abgeleiteten Klasse eine Nachrichtenzuordnung und die Nachrichtenhandlerfunktionen. Sie können Ihre Klasse jetzt auf drei verschiedene Arten verwenden:

- [Erstellen eines Fensters basierend auf einer neuen Windows-Klasse](#_atl_creating_a_window_based_on_a_new_windows_class)

- [Superklasse einer vorhandenen Windows-Klasse](#_atl_superclassing_an_existing_windows_class)

- [Unterklasse eines vorhandenen Fensters](#_atl_subclassing_an_existing_window)

## <a name="creating-a-window-based-on-a-new-windows-class"></a><a name="_atl_creating_a_window_based_on_a_new_windows_class"></a>Erstellen eines Fensters basierend auf einer neuen Windows-Klasse

`CWindowImpl`enthält [DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class) das DECLARE_WND_CLASS-Makro, um Windows-Klasseninformationen zu deklarieren. Dieses Makro implementiert `GetWndClassInfo` die Funktion, die [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) verwendet, um die Informationen einer neuen Windows-Klasse zu definieren. Wenn `CWindowImpl::Create` aufgerufen wird, wird diese Windows-Klasse registriert und ein neues Fenster erstellt.

> [!NOTE]
> `CWindowImpl`übergibt NULL `DECLARE_WND_CLASS` an das Makro, was bedeutet, dass ATL einen Windows-Klassennamen generiert. Um Ihren eigenen Namen anzugeben, übergeben `CWindowImpl`Sie eine Zeichenfolge an DECLARE_WND_CLASS in der -derived-Klasse.

## <a name="example"></a>Beispiel

Im Folgenden finden Sie ein Beispiel für eine Klasse, die ein Fenster implementiert, das auf einer neuen Windows-Klasse basiert:

[!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]

Um ein Fenster zu erstellen, erstellen Sie eine Instanz von, `CMyWindow` und rufen Sie dann die `Create` Methode auf.

> [!NOTE]
> Um die standardmäßigen Windows-Klasseninformationen `GetWndClassInfo` zu überschreiben, implementieren `CWndClassInfo` Sie die Methode in der abgeleiteten Klasse, indem Sie die Member auf die entsprechenden Werte festlegen.

## <a name="superclassing-an-existing-windows-class"></a><a name="_atl_superclassing_an_existing_windows_class"></a>Superklasse einer vorhandenen Windows-Klasse

Mit [dem DECLARE_WND_SUPERCLASS-Makro](reference/window-class-macros.md#declare_wnd_superclass) können Sie ein Fenster erstellen, in dem eine vorhandene Windows-Klasse überklassenwird. Geben Sie dieses `CWindowImpl`Makro in der -derived-Klasse an. Wie jedes andere ATL-Fenster werden Nachrichten von einer Meldungszuordnung verarbeitet.

Wenn Sie DECLARE_WND_SUPERCLASS verwenden, wird eine neue Windows-Klasse registriert. Diese neue Klasse entspricht der vorhandenen Klasse, die Sie angeben, `CWindowImpl::WindowProc` ersetzt jedoch die Fensterprozedur durch (oder durch Ihre Funktion, die diese Methode außer Kraft setzt).

## <a name="example"></a>Beispiel

Im Folgenden finden Sie ein Beispiel für eine Klasse, die die Standard-Edit-Klasse überlagert:

[!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]

Um das übergeordnete Bearbeitungsfenster zu erstellen, `CMyEdit` erstellen Sie `Create` eine Instanz von, und rufen Sie dann die Methode auf.

## <a name="subclassing-an-existing-window"></a><a name="_atl_subclassing_an_existing_window"></a>Unterklassen eines vorhandenen Fensters

Um ein vorhandenes Fenster unterzuklassieren, leiten Sie eine Klasse aus `CWindowImpl` und deklarieren Sie eine Nachrichtenzuordnung, wie in den beiden vorherigen Fällen. Beachten Sie jedoch, dass Sie keine Windows-Klasseninformationen angeben, da Sie ein bereits vorhandenes Fenster unterklassigen.

Anstatt `Create`aufzurufen, `SubclassWindow` rufen Sie das Handle auf, und übergeben Sie es an das vorhandene Fenster, das Sie unterklassen möchten. Sobald das Fenster unterklassifiziert ist, `CWindowImpl::WindowProc` verwendet es (oder Ihre Funktion, die diese Methode überschreibt), um Nachrichten an die Nachrichtenzuordnung weiterzuleiten. Um ein unterklassiertes Fenster von `UnsubclassWindow`Ihrem Objekt zu trennen, rufen Sie auf. Die ursprüngliche Fensterprozedur des Fensters wird dann wiederhergestellt.

## <a name="see-also"></a>Siehe auch

[Implementieren eines Fensters](../atl/implementing-a-window.md)
