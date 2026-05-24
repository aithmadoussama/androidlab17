# TP Android — Broadcast Receivers en Java

## 📌 Objectif du TP

Ce TP a pour objectif de comprendre le fonctionnement des **Broadcast Receivers** sous Android en Java.

L’application permet de :

- Écouter les changements du mode avion
- Envoyer et recevoir un broadcast personnalisé
- Utiliser un receiver statique au démarrage du téléphone
- Manipuler les `Intent` et `IntentFilter`

---

# 🛠️ Technologies utilisées

- Java
- Android Studio
- Android SDK
- BroadcastReceiver
- Intent / IntentFilter

---

# 📁 Structure du projet

```bash
lab17/
│
├── app/
│   ├── src/main/java/com/example/lab17/
│   │   ├── MainActivity.java
│   │   ├── AirplaneModeReceiver.java
│   │   ├── BootReceiver.java
│   │   └── CustomEventReceiver.java
│   │
│   ├── res/layout/
│   │   └── activity_main.xml
│   │
│   └── AndroidManifest.xml
```

---

# 📱 Fonctionnalités de l’application

## 1️⃣ Receiver dynamique du mode avion

L’utilisateur peut :

- Activer le receiver
- Désactiver le receiver
- Recevoir une notification Toast lorsque le mode avion change

### Classe utilisée

```java
AirplaneModeReceiver.java
```

### Broadcast écouté

```java
Intent.ACTION_AIRPLANE_MODE_CHANGED
```

---

## 2️⃣ Envoi d’un Custom Broadcast

L’application envoie un événement personnalisé :

```java
com.example.receiverdemo.CUSTOM_EVENT
```

Le receiver correspondant récupère le message et affiche un `Toast`.

### Classe utilisée

```java
CustomEventReceiver.java
```

---

## 3️⃣ Receiver statique au démarrage du téléphone

L’application possède un receiver qui écoute :

```java
Intent.ACTION_BOOT_COMPLETED
```

Lorsque le téléphone démarre :

- un message Toast est affiché

### Classe utilisée

```java
BootReceiver.java
```

---

# 🧠 Explication des fichiers Java

---

## 📄 MainActivity.java

Cette activité :

- initialise les boutons
- active/désactive le receiver dynamique
- envoie le custom broadcast

### Méthodes principales

### `toggleAirplaneReceiver()`

Permet :

- d’enregistrer le receiver
- de désenregistrer le receiver

avec :

```java
registerReceiver()
```

et

```java
unregisterReceiver()
```

---

### `sendCustomBroadcast()`

Envoie un broadcast personnalisé :

```java
Intent intent = new Intent("com.example.receiverdemo.CUSTOM_EVENT");
sendBroadcast(intent);
```

---

## 📄 AirplaneModeReceiver.java

Cette classe hérite de :

```java
BroadcastReceiver
```

Elle détecte les changements du mode avion.

### Méthode principale

```java
onReceive()
```

Cette méthode est exécutée automatiquement lorsqu’un broadcast est reçu.

---

## 📄 CustomEventReceiver.java

Ce receiver :

- reçoit le custom broadcast
- récupère le message envoyé
- affiche un Toast

---

## 📄 BootReceiver.java

Receiver statique qui s’exécute :

- après le démarrage du téléphone

---

# 🖼️ Interface graphique

Le fichier :

```xml
activity_main.xml
```

contient :

- un titre
- un TextView d’état
- un bouton pour le receiver avion
- un bouton pour envoyer le custom broadcast

---

# ▶️ Exécution du projet

## Étapes

### 1️⃣ Ouvrir Android Studio

### 2️⃣ Importer le projet

```bash
File → Open
```

### 3️⃣ Synchroniser Gradle

### 4️⃣ Exécuter l’application

```bash
Run ▶
```

---

# 🧪 Tests à réaliser

## ✅ Test 1 — Receiver mode avion

1. Activer le receiver
2. Activer/Désactiver le mode avion
3. Vérifier l’apparition du Toast

---

## ✅ Test 2 — Custom Broadcast

1. Cliquer sur :

```text
Envoyer Custom Broadcast
```

2. Vérifier le message reçu

---

## ✅ Test 3 — Boot Receiver

1. Redémarrer l’émulateur ou le téléphone
2. Vérifier l’exécution du receiver

---

# 📚 Concepts appris

À travers ce TP, nous avons appris :

- le fonctionnement des Broadcast Receivers
- la différence entre receiver dynamique et statique
- l’utilisation des Intent
- l’utilisation des IntentFilter
- la communication entre composants Android

---

# ✅ Conclusion

Ce TP permet de maîtriser les bases des Broadcast Receivers sous Android.

L’application démontre :

- l’écoute des événements système
- l’envoi de broadcasts personnalisés
- la réception des événements Android
- la gestion dynamique des receivers

Ce mécanisme est très utilisé dans les applications Android modernes.

---

