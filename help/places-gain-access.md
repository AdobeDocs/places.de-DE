---
title: 'Zugriff auf den Places Service '
description: In diesem Abschnitt erfahren Sie, wie Sie einen Benutzer zu "Orte-Dienst"und "Erlebnisplattformstart"hinzufügen, damit der Benutzer auf den Orte-Dienst zugreifen kann.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---

# Zugriff auf den Places Service {#adding-user-launch-places}

Sie können auf den Orte-Dienst über das Schnellzugriffsmenü in der [Adobe Experience Cloud-Startseite](https://experience.adobe.com)zugreifen.
Wenn Ihre Benutzer-ID Zugriff hat, wird das Symbol &quot;Orte-Dienst&quot;wie unten beschrieben angezeigt:

![Schnellzugriff](/help/assets/quick-access.png)

Sie können auch über das Menü &quot;Adobe Experience Platform&quot;auf den Places-Dienst zugreifen:

![Menü &quot;Erlebnisplattform&quot;](/help/assets/exp-platform-menu-sm.png)

Wenn Sie den Orte-Dienst in keinem dieser Menüs sehen, wenden Sie sich an einen Administrator in Ihrem Unternehmen, um Ihre Benutzer-ID dem Orte-Core-Dienst in der Admin-Konsole hinzuzufügen.

## Hinzufügen eines Benutzers zum Start des Places-Dienstes und der Experience Platform

Damit Benutzer auf die [Experience Platform Launch-Benutzeroberfläche](https://launch.adobe.com)zugreifen können, müssen sie als Benutzer dem Places Core Service in der Admin-Konsole hinzugefügt werden. Damit Benutzer Zugriff auf Experience Platform Launch haben, mobile Eigenschaften konfigurieren und Orte mit dem Adobe Experience Platform SDK verwenden können, müssen sie in der Admin-Konsole zum Experience Platform Launch hinzugefügt und die folgenden Berechtigungen für Experience Platform Launch erhalten:

* Alle Eigenschaftsrechte:
   * Entwickeln
   * Genehmigen
   * Veröffentlichen Sie
   * Erweiterungen verwalten
   * Verwalten von Umgebungen
* Berechtigung &quot;Eigenschaften verwalten&quot;unter &quot;Unternehmensrechte&quot;

Wenn Sie zum ersten Mal einen Benutzer hinzufügen, führen Sie die folgenden Schritte aus, um dem Experience Platform Launch and Places Service Benutzer hinzuzufügen. Wenn Sie zuvor Benutzer hinzugefügt haben, werden möglicherweise mehrere Profile angezeigt. Wählen Sie daher das richtige Profil aus.

>[!IMPORTANT]
>
>Nur Organisationsadministratoren können auf die Admin-Konsole zugreifen und die Benutzer hinzufügen.

### 1. Stellen Sie sicher, dass die Bereitstellung des Orts-Dienstes und des Erlebnisplattformstarts erfolgt.

1. Melden Sie sich bei Ihrer Experience Cloud-Organisation an.
1. Klicken Sie oben rechts auf den Experience Cloud-Shell-Umschalter.

   ![Shell-Umschalter](/help/assets/places_shell_switcher1.png)

1. Unter **[!UICONTROL Platform]**klicken Sie auf**[!UICONTROL Administration]**.

   Wenn die Liste keine **Verwaltung** enthält, sind Sie kein Administrator. Sie müssen sich an Ihren Organisationsadministrator wenden, um dieses Verfahren abzuschließen.

1. Klicken Sie auf der Seite &quot;Experience Cloud-Verwaltung&quot;auf der **[!UICONTROL Admin Console]**Karte auf**[!UICONTROL Take me there]**.

1. Wenn Sie in der Admin-Konsole Zugriff auf mehrere Organisationen haben, überprüfen Sie, ob rechts oben auf der Seite die richtige Organisation ausgewählt ist.

   Dies ist die Organisation, der Sie Ihre Benutzer hinzufügen werden. Wenn die richtige Reihenfolge nicht ausgewählt wurde, klicken Sie auf das Org und wählen Sie das Org aus der Dropdownliste aus.

   >[!IMPORTANT]
   >
   >Wenn Sie keinen Zugriff auf eine Organisation haben, haben Sie keinen Administratorzugriff auf diese Organisation.

1. Vergewissern Sie sich, dass die Karten für **[!UICONTROL Adobe Experience Platform Launch]**und**[!UICONTROL Places Core Services]** angezeigt werden.

   ![](/help/assets/places_provisioned1.png)

   Wenn sie angezeigt werden, wurden für Ihr Unternehmen der Orte-Dienst und der Erlebnisplattformstart bereitgestellt. Wenn sie nicht angezeigt werden, müssen sie für Ihr Unternehmen bereitgestellt werden.


### 2. Einrichten des Profils und Hinzufügen der Berechtigungen

1. Richten Sie ein Erlebnisplattformstartprofil ein, das Benutzern, die dem Profil hinzugefügt wurden, den Einsatz von Experience Platform Launch und seinen mobilen Eigenschaften mit dem Experience Platform SDK ermöglicht.

   a. Klicken Sie in der Menüleiste auf **[!UICONTROL Product]**.

   b. Klicken Sie im linken Bereich in der Liste der Produkte auf **[!UICONTROL Adobe Experience Platform Launch]**.

   * Die Erlebnisplattformstartprofile werden rechts angezeigt.
   * Experience Platform Launch hat ein Standardprofil namens *Launch - (Organisationsname)* .

      Wenn Sie zuvor Benutzer zu Experience Platform Launch hinzugefügt haben, werden möglicherweise mehrere Profile aufgelistet.

1. Wählen Sie das richtige Profil aus:

   a. Klicken Sie auf den Namen des Standardprofils.

   b. Klicken Sie auf die **[!UICONTROL Permissions]**Registerkarte.

   c. Klicken Sie **[!UICONTROL Edit]**neben**[!UICONTROL Property Rights]**.

   d. Klicken Sie im linken Fensterbereich auf **[!UICONTROL + Add all]**.

   Durch diesen Schritt werden alle verfügbaren Berechtigungen in die Liste der enthaltenen Berechtigungen verschoben.

   e. Klicken Sie auf **[!UICONTROL Company Rights]**.

   f. Klicken Sie im linken Fensterbereich auf **[!UICONTROL + Manage Properties]**.

   g. Klicken Sie auf **[!UICONTROL Save]**.

>[!IMPORTANT]
>
>Für den Orte-Dienst gibt es ein Standardprofil, Sie müssen jedoch keine Berechtigungen hinzufügen.

Sie haben dem erstellten Profil erfolgreich Berechtigungen hinzugefügt.

### 3. Benutzer oder Entwickler zu den Profilen &quot;Platzierungsdienst&quot;und &quot;Experience Platform Launch&quot;hinzufügen

Sie können einen Benutzer und/oder einen Entwickler zu den Profilen &quot;Orts-Service&quot;und &quot;Experience-Plattform-Start&quot;hinzufügen.

### Einen Benutzer hinzufügen

So fügen Sie Ihren Profilen &quot;Platzierungsdienst&quot;und &quot;Experience Platform Launch&quot;einen Benutzer hinzu:

1. Fügen Sie dem Erlebnis-Plattform-Startprofil einen Benutzer hinzu.

   a. Klicken Sie in der Menüleiste auf **[!UICONTROL Overview]**.

   b.Überprüfen Sie auf der **[!UICONTROL Adobe Experience Platform Launch]**Karte Folgendes:

   * Am unteren Rand der Karte werden zwei Punkte angezeigt.
   * Der Punkt links ist schwarz.

      Wenn der Punkt auf der rechten Seite schwarz ist, können Sie nur Entwickler hinzufügen. Um einen Benutzer hinzuzufügen, klicken Sie auf den Punkt links.
   c. Klicken Sie auf **[!UICONTROL + Add Users]**.

   d. Geben Sie die Adobe ID des Benutzers ein.

   e. Führen Sie einen der folgenden Schritte aus:

   * Wenn Sie einen neuen Benutzer hinzufügen, klicken Sie auf **[!UICONTROL New user]**und geben Sie den Vor- und Nachnamen des Benutzers ein.
   * Wenn Sie einen vorhandenen Benutzer hinzufügen, klicken Sie auf den angezeigten Benutzernamen.
   f. Wählen Sie in der **[!UICONTROL Please select a profile for this product]**Dropdownliste das Profil aus, das Sie zuvor bearbeitet haben.

   g. Klicken Sie auf **[!UICONTROL Save]**.

1. Fügen Sie einem Benutzer hinzu **[!UICONTROL Places Core Services]**.

   >[!TIP]
   >
   >Derzeit haben alle Benutzer des Places-Dienstes dieselben Berechtigungen, sodass Sie die Berechtigungen nicht bearbeiten müssen.

   a.Überprüfen Sie auf der **[!UICONTROL Places Core Services]**Karte Folgendes:

   * Am unteren Rand der Karte werden zwei Punkte angezeigt.
   * Der Punkt links ist schwarz.
   b. Klicken Sie auf **[!UICONTROL + Assign Users]**.

   c. Geben Sie die Adobe ID des Benutzers ein.

   d. Führen Sie einen der folgenden Schritte aus:

   * Wenn Sie einen neuen Benutzer hinzufügen, klicken Sie auf **[!UICONTROL New user]**und geben Sie den Vor- und Nachnamen des Benutzers ein.
   * Wenn Sie einen vorhandenen Benutzer hinzufügen, klicken Sie auf den angezeigten Benutzernamen.
   e. Wählen Sie in der **[!UICONTROL Please select a profile for this product]**Dropdownliste das Profil Orte aus.

   f. Klicken Sie auf **[!UICONTROL Save]**.

### Hinzufügen eines Entwicklers

Für Benutzer, die auch Zugriff auf die Web Service API benötigen, müssen Sie diese als Entwickler hinzufügen.

So fügen Sie einen Entwickler hinzu:

1. Überprüfen Sie auf der **[!UICONTROL Places Core Services]**Karte Folgendes:

   * Am unteren Rand der Karte werden zwei Punkte angezeigt.
   * Klicken Sie auf den Punkt rechts, damit er unten auf der Karte angezeigt **[!UICONTROL Assign Developers]**wird.

1. Klicken Sie auf **[!UICONTROL + Assign Developers]**.

1. Geben Sie die Adobe ID des Benutzers ein.

1. Führen Sie einen der folgenden Schritte aus:

   * Wenn Sie einen neuen Benutzer hinzufügen, klicken Sie auf **[!UICONTROL New user]**und geben Sie den Vor- und Nachnamen des Benutzers ein.
   * Wenn Sie einen vorhandenen Benutzer hinzufügen, klicken Sie auf den angezeigten Benutzernamen.

1. Wählen Sie in der **[!UICONTROL Please select a profile for this product]**Dropdownliste das Profil Orte-Dienst aus.

1. Klicken Sie auf **Speichern**.

Benutzer erhalten eine E-Mail, in der sie darauf hingewiesen werden, dass sie Zugriff auf Experience Platform Launch haben. They can can log in to the [Experience Platform Launch](https://launch.adobe.com) or the [Places Service](https://places.adobe.com) UIs for this organization. Wenn Sie Schritt 4 im Prozess **Entwickler hinzufügen** abgeschlossen haben, kann sich der Benutzer auch bei der [Adobe I/O-Konsole](https://console.adobe.io) anmelden, um eine Places-Integration zu erstellen und die Places-REST-API zu verwenden.
