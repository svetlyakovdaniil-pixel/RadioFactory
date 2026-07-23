# Dashboard (Update 10)

## Backend Contract

Dashboard never derives business state locally.

It only renders confirmed backend state.

Every operation returns:
- requestId
- status
- message
- timestamp
- optional payload

The UI must correlate updates using requestId.
