# EDGE Queue / Token System

Added a simple queue board at `/queue` for authenticated EDGE/Bull Ring admins.

## Flow

For each existing `edge_activities` sub-event and selected round:

`WAITING ROOM -> EVALUATION ROOM 1 / EVALUATION ROOM 2 -> COMPLETED`

The board shows:
- Token number
- Team name
- Team code
- Who is waiting
- Who is in Evaluation Room 1
- Who is in Evaluation Room 2
- The next waiting token

## Rounds

Round 1 and Round 2 can be selected. A queue is created automatically the first time that activity/round is opened.

## Team source

Teams are automatically pulled from the existing `edge_event_participations` records for the selected activity. No duplicate team setup is required.

## Actions

- Send next token to Evaluation Room 1
- Send next token to Evaluation Room 2
- Complete the team in either evaluation room
- Reset the selected round queue

The backend prevents sending a second team into an occupied evaluation room.

## Realtime

Queue changes broadcast through the existing Pusher `edge-global` channel using `queue-updated`, so other open queue screens refresh automatically when credentials are configured.
