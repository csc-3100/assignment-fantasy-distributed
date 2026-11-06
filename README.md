# CSC 3100 — Distributed Fantasy Adventure (A04)

[![Java CI](https://github.com/csc-3100/assignment-fantasy-distributed/actions/workflows/ci.yml/badge.svg)](https://github.com/csc-3100/assignment-fantasy-distributed/actions/workflows/ci.yml)

**Instructor starter template — intentionally incomplete.** The project compiles, but several acceptance tests initially fail. Complete the TODOs; do not change instructor tests to make them pass.

## Team workflow
Two students per team, one repository created using **Use this template**. One substantive pull request **per assigned feature**, authored by its owner and approved by the teammate. PR descriptions are the development log: responsibility, changes, tests, and evidence. CI must pass before merge.

**Partner A:** GUI + Observer; character/equipment; game logic tests. **Partner B:** MQTT integration; console; message tests and Docker demonstration. Both participate in integration, reviews, and testing. Each partner also writes two additional meaningful tests.

## Run
- Java 21 and Maven: `mvn clean verify` (initially fails by design).
- Desktop Swing: `mvn exec:java`.
- Docker interactive console: `docker compose run --build --rm game`.
- Change identity/team: `PLAYER=bob TEAM=team01 docker compose run --build --rm game`.
- For desktop, set environment variables `PLAYER`, `TEAM`, and optionally `MQTT_BROKER`.

The provided Dockerfile, Compose file, and CI workflow are infrastructure. **Students implement the application behavior.** The console must accept one-step `w/a/s/d` movement, `sword`, `shield`, and `quit`. The GUI must show named players and equipment and use Observer to repaint. MQTT uses `csc3100/a04/<team>/players/<username>`, QoS 1, and retained player state. Remote updates must not be republished. Disconnected players remain at their last known positions; retained state does **not** prove a player is online.

## Required screenshot
Place `docs/screenshot.png` in the repository and embed it here after implementation. Show **at least two named players** in the Swing game board.

## Testing
Instructor tests cover Factory, Decorator, movement, Observer, JSON, and remote synchronization. Write four additional tests (two per student) for documented edge cases. Unit tests must not require a live MQTT broker. Run a separate manual two-client MQTT demonstration.

## Next week's individual lab
Be ready to identify where MQTT messages arrive; trace model updates; explain Observer GUI notifications; run and explain a JUnit test; and make a small instructor-requested code change. This is assessed separately from A04 homework.

## Design decisions (complete as a team)
Explain why the model is independent of Swing, why MQTT is separated from game logic, how Decorator is used, and how tests avoid the public broker.
