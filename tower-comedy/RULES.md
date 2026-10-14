# Rules

Host is the single source of truth. First implementation runs the full night with only the host device. Performer and audience phones are optional clients that join later.

## Interfaces

- Host: owns lineup, current set, timer, scoring window, prize status, named buckets, and all overrides.
- Performer: receives published state. Can send ready status only. Cannot change order or timers.
- Audience / Patron: receives published state. Can send votes (when window open) and tips (when linked). Cannot change order or timers.

## Join and Association

QR code is the required mechanism to join the active session for both performers and patrons. Host displays the session QR. Scanning opens the web page for that session. Host sees the new join and must explicitly accept and link it.

Cash-first organic path:

1. Patron hands cash.
2. Host asks for a name and creates a named bucket. Cash is recorded against that name with timestamp immediately.
3. Host asks them to scan the QR before they sit.
4. When the phone joins, host links that specific join to the existing named bucket.
5. Phone stores a local file with session ID and named bucket. Reconnect presents the local file so the host can re-accept the same association without losing the balance or history.

People without phones remain named cash buckets managed entirely by the host. No money is lost on disconnect.

## Votes

Votes are fully anonymous. No one sees which patron cast which vote. Claims of "I voted for you" stay unprovable.

Two-item minimum generally entitles a patron to three votes for the night (one per set). Host opens a short anonymous vote window after each set. Each eligible patron casts at most one vote per set. Performers cannot vote for their own set.

Each set receives one point per vote. The set with the most votes receives a fixed winner's bonus. That ranking can convert into prize money under published rules. Votes do not reveal individual sources.

With only three sets (or one main event) there is no multi-round creative game. No acronym prompts. No face-off rounds. Sequential vote windows after each set are sufficient. Round-robin performer voting is not used.

## Tips

Tips are fully disclosed and independent of votes. Every tip records the named patron, amount, exact timestamp, and current performer. Performer can later see who sent what and when, aligned with the night's video recording.

Tips can arrive in real time during a set for feedback (for example after a punchline). Host can also enter cash tips by hand against a named bucket with the current timestamp.

Tips do not affect the anonymous vote ranking. Votes do not automatically become tips.

## Claps

Private clap button on the joined patron page. Tap records timestamp and current performer against that patron's own record only. Used for the patron's later personal review of how much they marked each performer. Not published to others. Not used for scoring or tips.

Optional room rule: tap the button before physical clapping. Aggregate clap count (host-controlled) can optionally drive a simple sound cue. Individual history stays private.

## Process Communication

Host publishes state changes. Joined clients subscribe and update. Only narrow writes return: performer ready status, patron votes (during open window), patron tips, and private claps. All validated by the host before any other client sees them. No direct performer-to-audience messaging. Timers are host-authoritative.
