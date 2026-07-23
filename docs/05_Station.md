# Station (Update 03)

## Lifecycle Responsibilities

Station отвечает только за принятие решений.

Она НЕ должна:
- выполнять HTTP-запросы к интерфейсу;
- рисовать UI;
- самостоятельно управлять другими Station.

## State Ownership

Только Station владеет:
- текущим состоянием;
- активным Broadcast;
- Pending LIVE Package;
- пользовательским намерением (Running/Stopped).

Никакой другой компонент не должен менять эти данные напрямую.
