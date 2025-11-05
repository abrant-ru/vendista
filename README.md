# Реализация на Python работы с терминалом Vendista в режиме Slave
[Описание протокола](https://wiki.vendista.ru/home/slave_protocol)

## Пример использования
```Python
import vendista
from queue import Queue

event_queue = Queue()
terminal = vendista.Vendista(serial_port=config["Port"], event_queue=event_queue, log_level=logging.INFO)

while True:
    event = event_queue.get()
    if event.get("sender") == terminal:
        if event.get("type") == vendista.Type.CARD_AUTH_RESULT:
            amount = event.get("amount")
```