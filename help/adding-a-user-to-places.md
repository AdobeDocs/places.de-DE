---
title: Hinzufügen eines Benutzers zu "Orte und Erlebnisplattformstart"
seo-title: Hinzufügen eines Benutzers zu "Orte und Erlebnisplattformstart"
description: 'Sie müssen Benutzer zum Orte-Core-Dienst hinzufügen, damit sie auf die Benutzeroberfläche "Orte"zugreifen können. '
seo-description: 'Sie müssen Benutzer zum Orte-Core-Dienst hinzufügen, damit sie auf die Benutzeroberfläche "Orte"zugreifen können. '
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Hinzufügen eines Benutzers zu "Orte und Erlebnisplattformstart" {#adding-user-launch-places}

Damit Benutzer auf die Benutzeroberfläche[des ](https://places.adobe.com)Startdienstes zugreifen können, müssen sie als Benutzer dem Orte-Core-Dienst in der Admin-Konsole hinzugefügt werden. Damit Benutzer Zugriff auf Experience Platform Launch haben, mobile Eigenschaften konfigurieren und Orte mit dem Adobe Experience Platform SDK verwenden können, müssen sie in der Admin-Konsole zum Experience Platform Launch hinzugefügt und die folgenden Berechtigungen für Experience Platform Launch erhalten:

* Alle Eigenschaftsrechte:
   * Entwickeln
   * Genehmigen
   * Veröffentlichen Sie
   * Erweiterungen verwalten
   * Verwalten von Umgebungen
* Berechtigung "Eigenschaften verwalten"unter "Unternehmensrechte"

Wenn Sie zum ersten Mal einen Benutzer hinzufügen, führen Sie die folgenden Schritte aus, um Benutzer zu Experience Platform Launch and Places hinzuzufügen. Wenn Sie zuvor Benutzer hinzugefügt haben, werden möglicherweise mehrere Profile angezeigt. Wählen Sie daher das richtige Profil aus.

>[!IMPORTANT]
>
>Nur Organisationsadministratoren können auf die Admin-Konsole zugreifen und die Benutzer hinzufügen.

## 1. Stellen Sie sicher, dass Orte und Erlebnisplattformstarts bereitgestellt wurden.

So überprüfen Sie, ob Orte und Erlebnisplattformstarts bereitgestellt wurden:

1. Melden Sie sich bei Ihrer Experience Cloud-Organisation an.
1. Klicken Sie oben rechts auf den Experience Cloud-Shell-Umschalter.

   ![Shell-Umschalter](/help/assets/places_shell_switcher1.png)

1. Klicken Sie unter **[!UICONTROL Platform]** auf **[!UICONTROL Administration]**.

   Wenn die Liste keine **Verwaltung** enthält, sind Sie kein Administrator. Sie müssen sich an Ihren Organisationsadministrator wenden, um dieses Verfahren abzuschließen.

1. Klicken Sie auf der Seite "Experience Cloud-Verwaltung"auf der **[!UICONTROL Admin Console]** Karte auf **[!UICONTROL Take me there]**.

1. Wenn Sie in der Admin-Konsole Zugriff auf mehrere Organisationen haben, überprüfen Sie, ob rechts oben auf der Seite die richtige Organisation ausgewählt ist.

   Dies ist die Organisation, der Sie Ihre Benutzer hinzufügen werden. Wenn die richtige Reihenfolge nicht ausgewählt wurde, klicken Sie auf das Org und wählen Sie das Org aus der Dropdownliste aus.

   >[!IMPORTANT]
   >
   >Wenn Sie keinen Zugriff auf eine Organisation haben, haben Sie keinen Administratorzugriff auf diese Organisation.

1. Überprüfen Sie, ob die Karten für **[!UICONTROL Adobe Experience Platform Launch]** und angezeigt **[!UICONTROL Places Core Services]** werden.

   ![](/help/assets/places_provisioned1.png)

   Wenn sie angezeigt werden, wurden Orte und Erlebnisplattformstarts für Ihr Unternehmen bereitgestellt. Wenn sie nicht angezeigt werden, müssen sie für Ihr Unternehmen bereitgestellt werden.

   >[!IMPORTANT]
   >
   >Während der Beta-Phase wird die Anforderung nach Abschluss der [Beta-Umfrage](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u)an das Provisioning-Team gesendet.

## 2. Einrichten des Profils und Hinzufügen der Berechtigungen

So richten Sie das Profil ein und fügen die Berechtigungen hinzu:

1. Richten Sie ein Erlebnisplattformstartprofil ein, das Benutzern, die dem Profil hinzugefügt wurden, den Einsatz von Experience Platform Launch und seinen mobilen Eigenschaften mit dem Experience Platform SDK ermöglicht.

   a. Klicken Sie in der Menüleiste auf **[!UICONTROL Product]**.

   b. Klicken Sie im linken Bereich in der Liste der Produkte auf **[!UICONTROL Adobe Experience Platform Launch]**.

   * Die Erlebnisplattformstartprofile werden rechts angezeigt.
   * Experience Platform Launch hat ein Standardprofil namens *Launch - (Organisationsname)* .

      Wenn Sie zuvor Benutzer zu Experience Platform Launch hinzugefügt haben, werden möglicherweise mehrere Profile aufgelistet.

2. Wählen Sie das richtige Profil aus:

   a. Klicken Sie auf den Namen des Standardprofils.

   b.Klicken Sie auf die **[!UICONTROL Permissions]** Registerkarte.

   c. Klicken Sie **[!UICONTROL Edit]** neben **[!UICONTROL Property Rights]**.

   d. Klicken Sie im linken Fensterbereich auf **[!UICONTROL + Add all]**.

   Durch diesen Schritt werden alle verfügbaren Berechtigungen in die Liste der enthaltenen Berechtigungen verschoben.

   e. Klicken Sie auf **[!UICONTROL Company Rights]**.

   f. Klicken Sie im linken Fensterbereich auf **[!UICONTROL + Manage Properties]**.

   g. Klicken Sie auf **[!UICONTROL Save]**.

>[!IMPORTANT]
>
>Für Orte gibt es ein Standardprofil, Sie müssen jedoch keine Berechtigungen hinzufügen.

Sie haben dem erstellten Profil erfolgreich Berechtigungen hinzugefügt.

## 3. Benutzer oder Entwickler zu den Startprofilen für Orte und Erlebnisplattformen hinzufügen

Sie können einen Benutzer und/oder einen Entwickler zu Ihren Startprofilen für Orte und Erlebnisplattformen hinzufügen.

## Einen Benutzer hinzufügen

So fügen Sie einen Benutzer zu den Profilen "Orte und Erlebnis-Plattform-Start"hinzu:

1. Fügen Sie dem Erlebnis-Plattform-Startprofil einen Benutzer hinzu.

   a. Klicken Sie in der Menüleiste auf **[!UICONTROL Overview]**.

   b.Überprüfen Sie auf der **[!UICONTROL Adobe Experience Platform Launch]** Karte Folgendes:

   * Am unteren Rand der Karte werden zwei Punkte angezeigt.
   * Der Punkt links ist schwarz.

      Wenn der Punkt auf der rechten Seite schwarz ist, können Sie nur Entwickler hinzufügen. Um einen Benutzer hinzuzufügen, klicken Sie auf den Punkt links.
   c. Klicken Sie auf **[!UICONTROL + Add Users]**.

   d. Geben Sie die Adobe ID des Benutzers ein.

   e. Führen Sie einen der folgenden Schritte aus:

   * Wenn Sie einen neuen Benutzer hinzufügen, klicken Sie auf **[!UICONTROL New user]** und geben Sie den Vor- und Nachnamen des Benutzers ein.
   * Wenn Sie einen vorhandenen Benutzer hinzufügen, klicken Sie auf den angezeigten Benutzernamen.
   f. Wählen Sie in der **[!UICONTROL Please select a profile for this product]** Dropdownliste das Profil aus, das Sie zuvor bearbeitet haben.

   g. Klicken Sie auf **[!UICONTROL Save]**.

2. Fügen Sie einem Benutzer hinzu **[!UICONTROL Places Core Services]**.

   >[!TIP]
   >
   >Derzeit haben alle Benutzer von Orten dieselben Berechtigungen, sodass Sie die Berechtigungen nicht bearbeiten müssen.

   a.Überprüfen Sie auf der **[!UICONTROL Places Core Services]** Karte Folgendes:

   * Am unteren Rand der Karte werden zwei Punkte angezeigt.
   * Der Punkt links ist schwarz.
   b. Klicken Sie auf **[!UICONTROL + Assign Users]**.

   c. Geben Sie die Adobe ID des Benutzers ein.

   d. Führen Sie einen der folgenden Schritte aus:

   * Wenn Sie einen neuen Benutzer hinzufügen, klicken Sie auf **[!UICONTROL New user]** und geben Sie den Vor- und Nachnamen des Benutzers ein.
   * Wenn Sie einen vorhandenen Benutzer hinzufügen, klicken Sie auf den angezeigten Benutzernamen.
   e. Wählen Sie in der **[!UICONTROL Please select a profile for this product]** Dropdownliste das Profil Orte aus.

   f. Klicken Sie auf **[!UICONTROL Save]**.

## Hinzufügen eines Entwicklers

Für Benutzer, die auch Zugriff auf die Places REST API benötigen, müssen Sie diese als Entwickler hinzufügen.

So fügen Sie einen Entwickler hinzu:

1. Überprüfen Sie auf der **[!UICONTROL Places Core Services]** Karte Folgendes:

   * Am unteren Rand der Karte werden zwei Punkte angezeigt.
   * Klicken Sie auf den Punkt rechts, damit er unten auf der Karte angezeigt **[!UICONTROL Assign Developers]** wird.

1. Klicken Sie auf **[!UICONTROL + Assign Developers]**.

1.  Geben Sie die Adobe ID des Benutzers ein.

1.  Führen Sie einen der folgenden Schritte aus:

   * Wenn Sie einen neuen Benutzer hinzufügen, klicken Sie auf **[!UICONTROL New user]** und geben Sie den Vor- und Nachnamen des Benutzers ein.
   * Wenn Sie einen vorhandenen Benutzer hinzufügen, klicken Sie auf den angezeigten Benutzernamen.

1. Wählen Sie in der **[!UICONTROL Please select a profile for this product]** Dropdownliste das Profil Location Service aus.

1. Klicken Sie auf **Speichern**.

Benutzer erhalten eine E-Mail, in der sie darauf hingewiesen werden, dass sie Zugriff auf Experience Platform Launch haben. Sie können sich beim [Experience Platform Launch](https://launch.adobe.com) oder der Benutzeroberfläche für [Orte](https://places.adobe.com) für diese Organisation anmelden. Wenn Sie Schritt 4 im Vorgang "Entwickler **hinzufügen** "abgeschlossen haben, kann sich der Benutzer auch bei der [Adobe-E/A-Konsole](https://console.adobe.io) anmelden, um eine Ortsintegration zu erstellen und die Places REST-API zu verwenden.
