---
name: Spielervorlage erweitern
index: 7
---

# Die Spielervorlage erweitern

In der Version der Java-Spielervorlage von der Software-Challenge
Homepage ist bereits eine Strategie implementiert, die RandomLogic. Man
kann jedoch auch noch beliebig viele eigene Strategien hinzufügen.

## Erstellen einer neuen Strategie

Die einfachste Möglichkeit ist, die Klasse `Logic` der Spielervorlage zu
kopieren und umzubenennen (alle Vorkommen von `Logic` durch den neuen
Klassennamen ersetzen). Der Vollständigkeit halber hier noch das
Vorgehen bei einer komplett neuen Klasse:

-   Erstellt eine neue Klasse (z.B. `MyLogic`), die das Interface
    `IGameHandler` implementiert:


```java
    public class MyLogic implements IGameHandler {
        private Starter client;
        private GameState gameState;
        private Player currentPlayer;
```
-   Erstellt einen Konstruktor, der eine Instanz des Starters erhält.
    Diese wird später noch gebraucht


```java
    public MyLogic(Starter client) {
        this.client = client;
    }
```
-   Implementiert die 5 Interface-Methoden


```java
    @Override
    public void gameEnded(GameResult result, PlayerColor color, String errorMessage) {
        // Hier muss nichts getan werden
    }

    @Override
    public void onUpdate(Player player, Player otherPlayer) {
        // Der Spieler wurde aktualisiert
        this.player = player;
    }

    @Override
    public void onUpdate(GameState gameState) {
        // Ein neuer Spielstatus, d.h. etwas ist geschehen. Deshalb
        // alles aktualisieren.
        this.gameState = gameState;
        this.player = gameState.getCurrentPlayer();
    }

    @Override
    public void sendAction(Move move) {
        // Einen Zug an den Server senden
        starter.sendMove(move);
    }

    @Override
    public void onRequestAction() {
        // Ich soll einen Zug machen
        Move move;
        // ... Hier muss die Logik rein, die einen Zug findet.
        sendAction(move);
    }
```
Nun kann die Strategie in der Methode `onRequestAction` (oder in eigenen
Klassen, die dort verwendet werden) implementiert werden.
