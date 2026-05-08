# Texas Hold'em Poker (Java)

A fully playable Texas Hold'em Poker game built in Java with a Swing GUI. Supports 2–8 players in a local pass-and-play format with full betting rounds, hand evaluation, showdown logic, and multi-hand gameplay.

**Authors:** Tyler Drake & Steven Kester

## Status
Feature-complete for local pass-and-play. Some edge-case bugs remain — see `BUGS.md`.

---

## Running the Game

### Run the JAR
```bash
java -jar hwx.jar
```

### Compile from Source
```bash
javac -cp class -d class src\cards\*.java src\game\*.java src\gui\app\*.java src\gui\integration\*.java src\gui\view\*.java src\players\*.java
```

### Repackage the JAR
```bash
jar cvfm hwx.jar MANIFEST.MF -C class . -C src . -C resources . README.txt
```
> Ensure `MANIFEST.MF` is present and the main entry point is set to `GUIGame`

---

## Game Features

- **2–8 players** with configurable starting chip counts (default: 1,000)
- **Rotating dealer button** each hand
- **Blinds:** Small Blind = 10, Big Blind = 20
- **Betting actions:** Fold, Check, Call, Raise (custom amount), All-In
- **Hand evaluation:** Royal Flush → High Card with pot splitting for ties
- **Card visibility:** Only the active player sees their cards face-up
- **Multi-hand gameplay:** Chip counts carry over between hands

---

## Major Components

| Component | Description |
|-----------|-------------|
| `GameEngine` | Core poker logic: dealing, betting, hand evaluation, showdown |
| `GUIListener` | Communication layer between Swing UI and GameEngine |
| `TablePanel / PlayerPanel / BoardPanel` | Graphical display of players, cards, pot, and dealer button |
| `ActionPanel` | Action buttons, raise dialog, and Next Hand button |
| `CardImageLoader` | Loads all 52 card PNGs |

---

## Implementation Notes

- `GameEngine` runs in a separate thread to prevent GUI freezing
- GUI waits for player actions using synchronized locks (no busy-waiting)
- GUI layout optimized for **1400×900** resolution

---

## Extra Features

- Custom raise amounts via GUI pop-up
- Variable player count (2–8)
- Dealer button indicator
- Winner label with semi-transparent background
- Dynamic hand ranking display (e.g. "Flush", "Two Pair")
- Card images displayed graphically

---

## Known Limitations

- Pass-and-play only (no AI opponents)
- GUI tested primarily at 1400×900 resolution

---

## Credits

Card images: [OpenGameArt — Playing Cards Vector PNG](https://opengameart.org/content/playing-cards-vector-png)
