---
title: 'TN026: DDX- und DDV-Routinen'
ms.date: 06/28/2018
f1_keywords:
- DDX
- DDV
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
ms.openlocfilehash: 711d433b51ca09836f372d09a11f86c28b82cce6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370347"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026: DDX- und DDV-Routinen

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

Dieser Hinweis beschreibt die DDX-Architektur (Dialog Data Exchange) und die DDV-Architektur (Dialog Data Validation). Außerdem wird beschrieben, wie Sie eine DDX_- oder DDV_-Prozedur schreiben und wie Sie ClassWizard erweitern können, um Ihre Routinen zu verwenden.

## <a name="overview-of-dialog-data-exchange"></a>Übersicht über Dialogdatenaustausch

Alle Dialogdatenfunktionen werden mit C++-Code ausgeführt. Es gibt keine speziellen Ressourcen oder magische Makros. Das Herzstück des Mechanismus ist eine virtuelle Funktion, die in jeder Dialogklasse überschrieben wird, die dialogiumär den Datenaustausch und die Validierung durchführt. Es ist immer in dieser Form zu finden:

```cpp
void CMyDialog::DoDataExchange(CDataExchange* pDX)
{
    CDialog::DoDataExchange(pDX);   // call base class

    //{{AFX_DATA_MAP(CMyDialog)
        <data_exchange_function_call>
        <data_validation_function_call>
    //}}AFX_DATA_MAP
}
```

Die SPEZIELLEN AFX-Kommentare im Sonderformat ermöglichen es ClassWizard, den Code innerhalb dieser Funktion zu suchen und zu bearbeiten. Code, der nicht mit ClassWizard kompatibel ist, sollte außerhalb der speziellen Formatkommentare platziert werden.

Im obigen \<Beispiel ist data_exchange_function_call> in der Form:

```cpp
DDX_Custom(pDX, nIDC, field);
```

und \<data_validation_function_call> ist optional und hat folgende Form:

```cpp
DDV_Custom(pDX, field, ...);
```

In jeder `DoDataExchange` Funktion können mehr als ein DDX_/DDV_-Paar enthalten sein.

Eine Liste aller Dialogdatenaustauschroutinen und Dialogdatenvalidierungsroutinen, die mit MFC bereitgestellt werden, finden Sie unter "afxdd_.h".

Dialogdaten sind genau das: `CMyDialog` Memberdaten in der Klasse. Es wird nicht in einer Struktur oder ähnlichem gespeichert.

## <a name="notes"></a>Notizen

Obwohl wir dies "Dialogdaten" nennen, sind alle `CWnd` Funktionen in jeder Klasse verfügbar, die von diesen abgeleitet enther iert wurde, und sind nicht auf Dialoge beschränkt.

Anfangswerte von Daten werden im Standard-C++-Konstruktor `//{{AFX_DATA_INIT` festgelegt, in der Regel in einem Block mit und `//}}AFX_DATA_INIT` Kommentaren.

`CWnd::UpdateData`ist der Vorgang, der die Initialisierung und `DoDataExchange`Fehlerbehandlung rund um den Aufruf von ausführt.

Sie können `CWnd::UpdateData` jederzeit anrufen, um Datenaustausch und -validierung durchzuführen. Standardmäßig `UpdateData`(TRUE) wird im `CDialog::OnOK` Standardhandler `UpdateData`und (FALSE) im `CDialog::OnInitDialog`Standard handler aufgerufen.

Die DDV_ Routine sollte sofort der DDX_ Routine für dieses *Feld*folgen.

## <a name="how-does-it-work"></a>Wie funktioniert es

Sie müssen folgendes nicht verstehen, um Dialogdaten zu verwenden. Wenn Sie jedoch verstehen, wie dies hinter den Kulissen funktioniert, können Sie Ihr eigenes Austausch- oder Validierungsverfahren schreiben.

Die `DoDataExchange` Memberfunktion ähnelt `Serialize` der Memberfunktion - sie ist für das Abrufen oder Festlegen von Daten in/von einem externen Formular (in diesem Fall Steuerelemente in einem Dialogfeld) von/zu Memberdaten in der Klasse verantwortlich. Der *pDX-Parameter* ist der Kontext für den `CArchive` Datenaustausch und ähnelt dem Parameter zu `CObject::Serialize`. Das *pDX* `CDataExchange` (ein Objekt) hat `CArchive` ein Richtungsflag ähnlich wie ein Richtungsflag:

- Wenn `!m_bSaveAndValidate`, laden Sie dann den Datenstatus in die Steuerelemente.

- Wenn `m_bSaveAndValidate`, legen Sie dann den Datenstatus aus den Steuerelementen fest.

Die Validierung `m_bSaveAndValidate` erfolgt nur, wenn festgelegt ist. Der Wert `m_bSaveAndValidate` von wird durch den `CWnd::UpdateData`PARAMETER BOOL auf bestimmt.

Es gibt drei `CDataExchange` weitere interessante Mitglieder:

- `m_pDlgWnd`: Das Fenster (in der Regel ein Dialogfeld), das die Steuerelemente enthält. Dadurch soll verhindert werden, dass Aufrufer der DDX_ und DDV_ globalen Funktionen 'this' an jede DDX/DDV-Routine übergeben müssen.

- `PrepareCtrl`, `PrepareEditCtrl`und : Bereitet ein Dialogsteuerelement für den Datenaustausch vor. Speichert das Handle dieses Steuerelements zum Festlegen des Fokus, wenn eine Überprüfung fehlschlägt. `PrepareCtrl`wird für Steuerelemente `PrepareEditCtrl` ohne Bearbeitung und für Bearbeitungssteuerelemente verwendet.

- `Fail`: Wird aufgerufen, nachdem ein Meldungsfeld angezeigt wurde, in dem der Benutzer auf den Eingabefehler hingewiesen wird. Diese Routine stellt den Fokus auf das letzte `PrepareCtrl` `PrepareEditCtrl`Steuerelement (den letzten Aufruf von oder ) wieder her und löst eine Ausnahme aus. Diese Memberfunktion kann sowohl von DDX_ als auch von DDV_ Routinen aufgerufen werden.

## <a name="user-extensions"></a>Benutzererweiterungen

Es gibt mehrere Möglichkeiten, den standardmäßigen DDX/DDV-Mechanismus zu erweitern. Ihre Möglichkeiten:

- Fügen Sie neue Datentypen hinzu.

    ```cpp
    CTime
    ```

- Fügen Sie neue Austauschverfahren (DDX_) hinzu.

    ```cpp
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);
    ```

- Fügen Sie neue Validierungsverfahren (DDV_) hinzu.

    ```cpp
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);
    // make sure time is in the future or past
    ```

- Übergeben Sie beliebige Ausdrücke an die Validierungsverfahren.

    ```cpp
    DDV_MinMax(pDX, age, 0, m_maxAge);
    ```

    > [!NOTE]
    > Solche beliebigen Ausdrücke können nicht von ClassWizard bearbeitet werden und sollten daher außerhalb der speziellen Formatkommentare verschoben werden (/AFX_DATA_MAP(CMyClass)).

Lassen `DoDialogExchange` Sie die Memberfunktion Conditionals oder andere gültige C++-Anweisungen mit intermixed Exchange- und Validierungsfunktionsaufrufen enthalten.

```cpp
//{{AFX_DATA_MAP(CMyClass)
DDX_Check(pDX, IDC_SEX, m_bFemale);
DDX_Text(pDX, IDC_EDIT1, m_age);
//}}AFX_DATA_MAP
if (m_bFemale)
    DDV_MinMax(pDX, age, 0, m_maxFemaleAge);
else
    DDV_MinMax(pDX, age, 0, m_maxMaleAge);
```

> [!NOTE]
> Wie oben gezeigt, kann dieser Code nicht von ClassWizard bearbeitet werden und sollte nur außerhalb der speziellen Formatkommentare verwendet werden.

## <a name="classwizard-support"></a>ClassWizard-Support

ClassWizard unterstützt eine Teilmenge von DDX/DDV-Anpassungen, indem Sie Ihre eigenen DDX_ und DDV_ Routinen in die ClassWizard-Benutzeroberfläche integrieren können. Dies ist nur dann kostengünstig, wenn Sie bestimmte DDX- und DDV-Routinen in einem Projekt oder in vielen Projekten wiederverwenden möchten.

Dazu werden spezielle Einträge in DDX vorgenommen. CLW (frühere Versionen von Visual C++ haben diese Informationen in APSTUDIO gespeichert. INI) oder in Ihrem Projekt . CLW-Datei. Die Sondereinträge können entweder im Abschnitt [Allgemeine Informationen] ihres Projekts eingegeben werden. CLW-Datei oder im Abschnitt [ExtraDDX] des DDX. CLW-Datei im Verzeichnis "Programmdateien" , Microsoft Visual Studio, "Visual C++" "bin". Möglicherweise müssen Sie den DDX erstellen. CLW-Datei, wenn sie noch nicht vorhanden ist. Wenn Sie die benutzerdefinierten DDX_/DDV_-Routinen nur in einem bestimmten Projekt verwenden möchten, fügen Sie die Einträge zum Abschnitt [Allgemeine Informationen] Ihres Projekts hinzu. STATTDESSEN CLW-Datei. Wenn Sie die Routinen für viele Projekte verwenden möchten, fügen Sie die Einträge dem Abschnitt [ExtraDDX] von DDX hinzu. CLW.

Das allgemeine Format dieser Sondereinträge ist:

> ExtraDDXCount=*n*

Wo *n* ist die Anzahl der ExtraDDX? Linien folgen, des Formulars

> ExtraDDX?=*Tasten*; *vb-keys*; *Prompt*; *Typ*; *initValue*; *DDX_Proc* [; *DDV_Proc*; *prompt1*; *arg1* [; *prompt2*; *fmt2*]]

Wo? ist eine Zahl 1 - *n,* die angibt, welcher DDX-Typ in der Liste, die definiert wird, angegeben wird.

Jedes Feld wird durch ein ';'-Zeichen begrenzt. Die Felder und ihr Zweck werden unten beschrieben.

- *Schlüssel*

  Eine Liste einzelner Zeichen, die angeben, für welches Dialogfeld diesen Variablentyp steuert.

  |Zeichen|Zulässige Kontrolle|
  |-|-|
  E | Bearbeiten
  C | Kontrollkästchen mit zwei Staaten
  c | Kontrollkästchen tri-state
  R | erster Optionsfeld in einer Gruppe
  L | Nicht sortiertes Listenfeld
  l | sortiertes Listenfeld
  M | Kombinationsfeld (mit Bearbeitungselement)
  N | nicht sortierte Dropliste
  n | sortierte Drop-Liste
  1 | Wenn die DDX-Einfügung zum Listenkopf hinzugefügt werden soll (Standard ist "Add to tail") Wird dies im Allgemeinen für DDX-Routinen verwendet, die die Eigenschaft "Control" übertragen.

- *vb-keys*

  Dieses Feld wird nur im 16-Bit-Produkt für VBX-Steuerelemente verwendet (VBX-Steuerelemente werden im 32-Bit-Produkt nicht unterstützt)

- *Eingabeaufforderung*

  Zeichenfolge, die in das Eigenschaftenkombinationsfeld einzufügen ist (keine Anführungszeichen)

- *type*

  Einzelner Bezeichner für den Typ, der in der Headerdatei ausgesendet werden soll. In unserem obigen Beispiel mit DDX_Time würde dies auf CTime gesetzt.

- *vb-keys*

  In dieser Version nicht verwendet und sollte immer leer sein

- *initValue*

  Anfangswert — 0 oder leer. Wenn sie leer ist, wird keine Initialisierungszeile in den Abschnitt "AFX_DATA_INIT" der Implementierungsdatei geschrieben. Ein leerer Eintrag sollte für C++-Objekte (z. `CString`B. , `CTime`usw.) verwendet werden, die über Konstruktoren verfügen, die eine korrekte Initialisierung gewährleisten.

- *DDX_Proc*

  Einzelbezeichner für die DDX_-Prozedur. Der C++-Funktionsname muss mit "DDX_" beginnen, darf jedoch \<nicht "DDX_" in die DDX_Proc>-Bezeichner s. Im obigen Beispiel \<wäre der DDX_Proc> Bezeichner Zeit. Wenn ClassWizard den Funktionsaufruf in die Implementierungsdatei im Abschnitt "AFX_DATA_MAP" schreibt, fügt er diesen Namen an DDX_ an und gelangt so zu DDX_Time.

- *Kommentar*

  Kommentar, der im Dialog für variable mit diesem DDX angezeigt wird. Platzieren Sie hier einen beliebigen Text, und stellen Sie in der Regel etwas bereit, das den Vorgang des DDX/DDV-Paares beschreibt.

- *DDV_Proc*

  Der DDV-Teil des Eintrags ist optional. Nicht alle DDX-Routinen verfügen über entsprechende DDV-Routinen. Oft ist es bequemer, die Validierungsphase als integralen Bestandteil der Übertragung einzubeziehen. Dies ist häufig der Fall, wenn Ihre DDV-Routine keine Parameter benötigt, da ClassWizard keine DDV-Routinen ohne Parameter unterstützt.

- *arg*

  Einzelbezeichner für die DDV_-Prozedur. Der C++-Funktionsname muss mit "DDV_" beginnen, darf \<jedoch nicht "DDX_" in die DDX_Proc>-Bezeichners aufnehmen.

  *auf arg* folgen 1 oder 2 DDV-Args:

  - *promptN*

      String, der über dem Bearbeitungselement platziert werden soll (mit & für Beschleuniger).

  - *fmtN*

      Formatzeichen für den arg-Typ, eines von:

      |Zeichen|type|
      |-|-|
      |d | INT|
      |u | unsigned int|
      |D | long int (d.h. lang)|
      |U | lange unsigniert (d. h. DWORD)|
      |f | float|
      |F | double|
      |s | Zeichenfolge|

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
