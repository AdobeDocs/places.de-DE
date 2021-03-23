---
title: 'Zugriff auf den Places Service '
description: In diesem Abschnitt erfahren Sie, wie Sie einen Benutzer zu "Orte-Dienst"und "Experience Platform Launch"hinzufügen, damit der Benutzer auf den Orte-Dienst zugreifen kann.
translation-type: tm+mt
source-git-commit: ecf50d67d4c08e79d9c3be64480f27d435fd7fcb
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 10%

---

# Zugriff auf den Places Service {#adding-user-launch-places}

Sie können auf den Orte-Dienst über das Schnellzugriffsmenü unter [Adobe Experience Cloud home](https://experience.adobe.com) zugreifen.
Wenn Ihre Benutzer-ID Zugriff hat, wird das Symbol &quot;Orte-Dienst&quot;wie unten beschrieben angezeigt:

![Schnellzugriffsmenü](/help/assets/quickaccess.png)

Sie können auch über das Menü Adobe Experience Platform auf den Ortsdienst zugreifen:

![Menü &quot;Experience Platform&quot;](/help/assets/solutionaccessmenu.png)

Wenn Sie den Orte-Dienst in keinem dieser Menüs sehen, wenden Sie sich an einen Administrator in Ihrem Unternehmen, um Ihre Benutzer-ID dem Orts-Core-Service in der Admin Console hinzuzufügen.

## Hinzufügen eines Benutzers zum Platzierungsdienst und Experience Platform Launch

Damit Benutzer auf die [Benutzeroberfläche des Experience Platform Launchs](https://launch.adobe.com) zugreifen können, müssen sie als Benutzer dem &quot;Orte-Hauptdienst&quot;in der Admin Console hinzugefügt werden. Damit Benutzer Zugriff auf Experience Platform Launch haben, mobile Eigenschaften konfigurieren und Orte mit dem Adobe Experience Platform SDK verwenden können, müssen sie dem Experience Platform Launch in der Admin Console hinzugefügt und die folgenden Berechtigungen für den Experience Platform Launch erhalten:

* Alle Eigenschaftsrechte:
   * Entwickeln
   * Genehmigen
   * Veröffentlichen Sie
   * Erweiterungen verwalten
   * Umgebungen verwalten
* Berechtigung &quot;Eigenschaften verwalten&quot;unter &quot;Firma-Rechte&quot;

Wenn Sie zum ersten Mal einen Benutzer hinzufügen, führen Sie die folgenden Schritte aus, um Benutzer zum Experience Platform Launch- und Ortungsdienst hinzuzufügen. Wenn Sie zuvor Benutzer hinzugefügt haben, werden möglicherweise mehrere Profil angezeigt. Wählen Sie daher das richtige Profil aus.

>[!IMPORTANT]
>
>Nur Organisationsadministratoren können auf die Admin Console zugreifen und die Benutzer hinzufügen.

### 1. Stellen Sie sicher, dass der Orte-Dienst und der Experience Platform Launch bereitgestellt wurden.

1. Melden Sie sich bei Ihrer Experience Cloud-Organisation an.
1. Klicken Sie oben rechts auf den Experience Cloud Shell-Umschalter.

   ![Shell-Umschalter](/help/assets/places_shell_switcher1.png)

1. Klicken Sie unter **[!UICONTROL Platform]** auf **[!UICONTROL Administration]**.

   Wenn **[!UICONTROL Administration]** in der Liste nicht angezeigt wird, sind Sie kein Administrator. Sie müssen sich an Ihren Organisationsadministrator wenden, um dieses Verfahren abzuschließen.

1. Klicken Sie auf der Seite &quot;Experience Cloud-Verwaltung&quot;auf der Karte **[!UICONTROL Admin Console]** auf **[!UICONTROL Nehmen Sie mich dort]**.

1. Wenn Sie in der Admin Console Zugriff auf mehrere Organisationen haben, überprüfen Sie, ob rechts oben auf der Seite das richtige Unternehmen ausgewählt ist.

   Dies ist die Organisation, der Sie Ihre Benutzer hinzufügen werden. Wenn die richtige Reihenfolge nicht ausgewählt wurde, klicken Sie auf das Org und wählen Sie das Org aus der Dropdown-Liste aus.

   >[!IMPORTANT]
   >
   >Wenn Sie keinen Zugriff auf eine Organisation haben, haben Sie keinen Administratorzugriff auf diese Organisation.

1. Vergewissern Sie sich, dass die Karten für **[!UICONTROL Adobe Experience Platform Launch]** und **[!UICONTROL Places – Zentrale Dienste]** angezeigt werden.

   ![](/help/assets/places_provisioned1.png)

   Wenn sie angezeigt werden, wurden Orte-Dienst und Experience Platform Launch für Ihr Unternehmen bereitgestellt. Wenn sie nicht angezeigt werden, müssen sie für Ihr Unternehmen bereitgestellt werden.


### 2. Einrichten des Profils und Hinzufügen der Berechtigungen

1. Richten Sie ein Experience Platform Launch-Profil ein, das Benutzern, die dem Profil hinzugefügt wurden, die Verwendung von Experience Platform Launch und seinen mobilen Eigenschaften mit dem Experience Platform SDK ermöglicht.

   a. Klicken Sie in der Menüleiste auf **[!UICONTROL Produkt]**.

   b. Klicken Sie im linken Bereich in der Liste von products auf **[!UICONTROL Adobe Experience Platform Launch]**.

   * Die Profile des Experience Platform Launchs werden rechts angezeigt.
   * Experience Platform Launch verfügt über ein standardmäßiges Profil mit dem Namen *Launch - (org name)* .

      Wenn Sie zuvor Benutzer zu Experience Platform Launch hinzugefügt haben, werden möglicherweise mehrere Profil aufgelistet.

1. Wählen Sie das richtige Profil aus:

   a. Klicken Sie auf den Namen des Standard-Profils.

   b. Klicken Sie auf die Registerkarte **[!UICONTROL Berechtigungen]**.

   c. Klicken Sie neben **[!UICONTROL Property-Rechte]** auf **[!UICONTROL Bearbeiten]**.

   d. Klicken Sie im linken Bereich auf **[!UICONTROL + Hinzufügen all]**.

   Durch diesen Schritt werden alle verfügbaren Berechtigungen auf die enthaltene Liste für Berechtigungen verschoben.

   e. Klicken Sie auf **[!UICONTROL Firma-Rechte]**.

   f. Klicken Sie im linken Bereich auf **[!UICONTROL + Eigenschaften verwalten]**.

   g. Klicken Sie auf **[!UICONTROL Speichern]**.

>[!IMPORTANT]
>
>Für den Orte-Dienst gibt es ein Standard-Profil, Sie müssen jedoch keine Berechtigungen hinzufügen.

Sie haben dem erstellten Profil erfolgreich Berechtigungen hinzugefügt.

### 3. hinzufügen eines Benutzers oder Entwicklers für die Profil &quot;Orte-Dienst&quot;und &quot;Experience Platform Launch&quot;

Sie können einen Benutzer und/oder einen Entwickler zu Ihren Profilen für den Places Service und den Experience Platform Launch hinzufügen.

### Hinzufügen von Benutzern

So fügen Sie Ihren Profilen &quot;Orte-Dienst&quot;und &quot;Experience Platform Launch&quot;einen Benutzer hinzu:

1. hinzufügen Sie einen Benutzer zum Experience Platform Launch-Profil.

   a. Klicken Sie in der Menüleiste auf **[!UICONTROL Übersicht]**.

   b. Überprüfen Sie auf der Karte **[!UICONTROL Adobe Experience Platform Launch]** Folgendes:

   * Am unteren Rand der Karte werden zwei Punkte angezeigt.
   * Der Punkt links ist schwarz.

      Wenn der Punkt auf der rechten Seite schwarz ist, können Sie nur Entwickler hinzufügen. Um einen Benutzer hinzuzufügen, klicken Sie auf den Punkt links.
   c. Klicken Sie auf **[!UICONTROL + Hinzufügen Benutzer]**.

   d. Geben Sie das Adobe ID des Benutzers ein.

   e. Führen Sie einen der folgenden Schritte aus:

   * Wenn Sie einen neuen Benutzer hinzufügen, klicken Sie auf **[!UICONTROL Neuer Benutzer]** und geben Sie den Vor- und Nachnamen des Benutzers ein.
   * Wenn Sie einen vorhandenen Benutzer hinzufügen, klicken Sie auf den Namen des Benutzers, der angezeigt wird.

   f. Wählen Sie in der Dropdown-Liste **[!UICONTROL Bitte ein Profil für dieses Produkt]** aus, das Profil, das Sie zuvor bearbeitet haben.

   g. Klicken Sie auf **[!UICONTROL Speichern]**.

1. hinzufügen eines Benutzers auf **[!UICONTROL Platziert Hauptdienste]**.

   >[!TIP]
   >
   >Derzeit haben alle Benutzer des Places-Dienstes dieselben Berechtigungen, sodass Sie die Berechtigungen nicht bearbeiten müssen.

   a. Überprüfen Sie auf der Karte **[!UICONTROL Platziert Core Services]** Folgendes:

   * Am unteren Rand der Karte werden zwei Punkte angezeigt.
   * Der Punkt links ist schwarz.

   b. Klicken Sie auf **[!UICONTROL + Benutzer zuweisen]**.

   c. Geben Sie das Adobe ID des Benutzers ein.

   d. Führen Sie einen der folgenden Schritte aus:

   * Wenn Sie einen neuen Benutzer hinzufügen, klicken Sie auf **[!UICONTROL Neuer Benutzer]** und geben Sie den Vor- und Nachnamen des Benutzers ein.
   * Wenn Sie einen vorhandenen Benutzer hinzufügen, klicken Sie auf den Namen des Benutzers, der angezeigt wird.

   e. Wählen Sie in der Dropdown-Liste **[!UICONTROL Bitte ein Profil für dieses Produkt]** aus, das Profil Orte.

   f. Klicken Sie auf **[!UICONTROL Speichern]**.

### Entwickler Hinzufügen

Für Benutzer, die auch Zugriff auf die Web Service API benötigen, müssen Sie diese als Entwickler hinzufügen.

So fügen Sie einen Entwickler hinzu:

1. Überprüfen Sie auf der Karte **[!UICONTROL Places – Zentrale Dienste]** Folgendes:

   * Am unteren Rand der Karte werden zwei Punkte angezeigt.
   * Klicken Sie auf den Punkt rechts, damit **[!UICONTROL Entwickler zuweisen]** unten auf der Karte angezeigt wird.

1. Klicken Sie auf **[!UICONTROL + Entwickler zuweisen]**.

1. Geben Sie die Adobe ID des Benutzers ein.

1. Führen Sie einen der folgenden Schritte aus:

   * Wenn Sie einen neuen Benutzer hinzufügen, klicken Sie auf **[!UICONTROL Neuer Benutzer]** und geben Sie den Vor- und Nachnamen des Benutzers ein.
   * Wenn Sie einen vorhandenen Benutzer hinzufügen, klicken Sie auf den Namen des Benutzers, der angezeigt wird.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Bitte ein Profil für dieses Produkt]** aus, das Profil &quot;Orte-Dienst&quot;.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

Benutzer erhalten eine E-Mail, in der sie darauf hingewiesen werden, dass sie Zugriff auf Experience Platform Launch haben. Sie können sich bei den [Experience Platform Launch](https://launch.adobe.com) oder [Platzierungsdienst](https://places.adobe.com)-UIs für diese Organisation anmelden. Wenn Sie Schritt 4 im Prozess **[!UICONTROL Entwickler hinzufügen]** abgeschlossen haben, kann sich der Benutzer auch bei der [Adobe I/O-Konsole](https://console.adobe.io) anmelden, um eine Places-Integration zu erstellen und die Places-REST-API zu verwenden.
